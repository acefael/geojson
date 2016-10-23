# The Daemon Module

This Smallworld&trade; Magik Module implements a Network Service
Shell.  It can be told to listen on a TCP Port to serve clients.
There are no default services. The `daemon_image` module has some
sample services.

## Network Protocol

The protocol is of course very simple.  The client invokes a service
and receives the response.  Invoking a service means sending the name
that the service is registered under in the daemon, followed by the
service parameters.  In the MSF, the daemon reads the service name and
invokes the service procedure.  The service procedure is responsible
for reading any method parameters and for sending the response.

In bits and bytes:

- The Service Invocation packet looks like this:

    | len | method-name | parameters |

    len: length of the service method name, in characters, sent as an
         unsigned 4-byte integer

    method-name: name that the the service is registered under in
                 `daemon.services`

    parameters: the bits and bytes needed by the service to do its
                thing

- The Service Response is even simpler:

    | len | response-bytes |

    len: length of response, in bytes, as 4-bytes unsigned integer.

    response-bytes: len-bytes

All data must be in a format suitable for the methods on the MSF's
external binary streams.  That is typically little endian and the
strings are in a format known to Java as UTF-16LE.
