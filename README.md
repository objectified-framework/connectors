# connectors

Connectors is a service offered by Objectified that allows users to connect to a specific
server via a proxy engine that makes requests to end connections on their behalf.

## Use cases

- Periodic Data Collection
- Mainframe communications to services via proxy
- Firewall-restricted communications to services

## Generation of connectors

Generation of connectors is done through OpenAPI specifications and auto-generation of
code for clients.

Endpoints are made via OpenAPI proxies and client libraries.  These libraries are
pre-compiled, pre-build and build as artifacts in GitHub, but can be hosted in private
repositories.

## Architecture

A connection to an AWS service might look like this:

```
-------     ----------------     ---------------------
- AWS - --> - Proxy Server - <-- - Firewalled Client -
-------     ----------------     ---------------------
                    |
                    v
           ------------------
           - Credentials DB -
           ------------------
```

In this example, a firewalled client can talk to AWS via a proxy server.  The proxy
server runs on an externally hosted server.  That Firewalled Client then talks to the
proxy server using a singular access certificate, which is validated on the server.
Once validated, credentials are retrieved for the client's access, and requests are made
to the end service (AWS) on the client's behalf.

Payloads are then sent back to the client in whatever format they request.
