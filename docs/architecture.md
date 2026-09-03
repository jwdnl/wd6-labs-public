# Public architecture

The WD6 Reticulum gateway is a single-purpose transport in an isolated public
service segment in Amsterdam. Only TCP port 4242 is published to the Internet.
The node has no route to WD6 management, storage or customer networks.

```text
Reticulum client
       |
       | TCPClientInterface or BackboneInterface
       v
rns.wd6.net:4242
       |
       | RNS transport and explicit backbone peers
       v
Public Reticulum network
```

Status data leaves the gateway through an outbound-only collector path. A
separate observer performs DNS, TCP and Reticulum protocol checks. Neither the
status site nor this repository is hosted on the public transport VM.

The Reticulum-native Git service uses the existing shared RNS instance. It does
not add an HTTP listener or another publicly forwarded IP port, and its public
repository group grants read access only.
