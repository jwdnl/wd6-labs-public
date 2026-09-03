# WD6 Labs

Public documentation and client examples for experimental network projects by
[WD6.NET](https://wd6.net) / AS20495.

## Project 01: Reticulum gateway

WD6 operates an experimental, best-effort Reticulum transport in Amsterdam.
It contributes connectivity to the public Reticulum network and publishes only
sanitised aggregate telemetry.

- Gateway: `rns.wd6.net:4242/tcp`
- Live status: [labs.wd6.net/reticulum](https://labs.wd6.net/reticulum)
- Location: Amsterdam, Netherlands
- Service level: experimental, best effort, no SLA

Copy [`reticulum/client.conf.example`](reticulum/client.conf.example) into the
`[interfaces]` section of your Reticulum configuration, or adapt the included
Backbone example on supported RNS versions.

## Repository scope

This repository intentionally contains public-facing material only:

- connection examples;
- a high-level architecture and security model;
- the public telemetry contract;
- public operational and disclosure information.

Private infrastructure addresses, inventories, credentials, identities, raw
logs, peer metadata and recovery material are excluded. A repository safety
workflow checks every push for common secret formats and private address space.

## Reticulum-native access

A read-only `rngit` and NomadNet mirror is being commissioned on the existing
WD6 Reticulum transport. Its destination will be added here after the public
fetch and write-denial tests pass.

Reticulum and `rngit` are documented at
[reticulum.network](https://reticulum.network/manual/git.html).

## Contact

Operational or abuse reports: [abuse@wd6.net](mailto:abuse@wd6.net)

No licence is granted for third-party reuse unless a file explicitly states
otherwise. The connection examples may be copied and adapted for use with the
WD6 public gateway.
