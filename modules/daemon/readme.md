# The Daemon Module

This Smallworld&copy; Magik Module implements a Network Service Shell.
It can be told to listen on a TCP Port to serve clients.
There are no default services. The daemon_image image module has some sample services.

## Network Protocol

The protocol is of course very simple.  The client invokes a service and receives the response.  Invoking a service means sending the name that the service is registered under in the daemon, followed by the service parameters.
