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

The [connection guide](reticulum/CONNECT.md) includes an end-to-end protocol
test, troubleshooting and an example for connecting a community or radio segment.
Operators can [discuss a bounded connection trial](mailto:abuse@wd6.net?subject=Reticulum%20community%20uplink).

## Repository scope

This repository intentionally contains public-facing material only:

- connection examples;
- a high-level architecture and security model;
- the public telemetry contract;
- public operational and disclosure information.

Private infrastructure addresses, inventories, credentials, private identity
material, raw logs, peer metadata and recovery material are excluded. A
repository safety workflow checks every push for common secret formats and
private address space.

The public tree is published automatically from a separately reviewed,
sanitised directory in the private operations repository. The publisher has a
repository-bound deploy key for this repository only; internal files are never
part of the synchronised source tree.

## Reticulum-native access

A read-only `rngit` and NomadNet mirror is available on the existing WD6
Reticulum transport. With RNS and the `git-remote-rns` helper installed:

```console
git clone rns://1304210b2ce0bf92ddac65ce2374885c/public/wd6-labs-public.git
```

- rngit destination: `1304210b2ce0bf92ddac65ce2374885c`
- NomadNet destination: `0e21c67830a5f6a2b6aef5b61c052d8a`

The public clone and explicit write-denial paths were tested from a separate
client profile on 3 September 2026. The mirror has no write, create, admin or
statistics permission and does not expose another IP listener.

The existing home observer also performs a read-only end-to-end check every
fifteen minutes and verifies whether the Reticulum mirror matches the public
GitHub source. The live status page exposes only reachability, freshness and
check age. This is a functional check outside the gateway VM, not a second
independent hosting site.

Reticulum and `rngit` are documented at
[reticulum.network](https://reticulum.network/manual/git.html).

## Contact

Community connections, operational or abuse reports:
[abuse@wd6.net](mailto:abuse@wd6.net). Include your software/version, the check
time with timezone and a short description of your network. Keep private keys,
credentials and user logs out of reports. An operator LXMF address will be
published only when its receiving and backup path are verified.

No licence is granted for third-party reuse unless a file explicitly states
otherwise. The connection examples may be copied and adapted for use with the
WD6 public gateway.
