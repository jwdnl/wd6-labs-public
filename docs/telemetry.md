# Public telemetry contract

The live status API publishes only aggregate operational evidence. Its current
document is available at:

`https://labs.wd6.net/api/v1/status/reticulum`

Published measurements include:

- gateway, listener, bootstrap and backbone state;
- software versions and process uptime;
- aggregate traffic, announce and path-request counters;
- queue pressure and coarse system utilisation;
- total known paths and sample age;
- aggregate bootstrap, non-bootstrap and client-contributed route counts;
- counts of distinct next hops and route-contributing sessions;
- a route-table phase that marks the first 30 minutes after an RNS restart as
  relearning.

The independence percentage is not a quality score. It is the current share of
known destinations learned outside the configured bootstrap. It can change
substantially while routes expire, reconnect or are relearned.

The public surface excludes source IP addresses, peer and interface hashes,
destination hashes, route contents, payloads, raw logs, stable user identifiers
and authenticated operator detail.
