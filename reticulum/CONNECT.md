# Connect through WD6 Amsterdam

WD6 offers an experimental public Reticulum transport at **rns.wd6.net,
TCP port 4242**, in Amsterdam / AS20495. Access is best effort, with no SLA.
Check [live status](https://labs.wd6.net/reticulum) before troubleshooting.

## An ordinary client

In an app that supports a custom TCP connection, enter the hostname and port
above. If you already manage an RNS config, add the active interface from
[client.conf.example](client.conf.example) under its existing `[interfaces]`
section. Choose one of the TCP or Backbone alternatives for WD6.

Keep `enable_transport = no` for a normal end-user client. Reconnect/restart
your app or shared RNS instance through its normal controls after saving.
Keep existing identities and storage; replacing them changes your addresses.
No extra incoming Internet port is needed for this outbound connection.

## Verify a real Reticulum path

With the RNS command-line tools installed, use the same config directory as
your running shared RNS instance. The commands below use RNS's default directory;
add `--config /your/config/directory` for a custom profile.

```console
rnstatus --all
rnprobe --timeout 10 -n 3 rnstransport.probe e52d5c08e59d1e33ae6495df36e01ffa
```

The WD6 interface should be connected and the probe should return three proofs
with RTT measurements. A successful TCP connect alone does not prove Reticulum
transport. The destination above is the gateway's probe service, not its
transport fingerprint or an LXMF messaging address. With several uplinks active,
the probe can use another route; an isolated client with only WD6 configured is
the strongest test of this specific connection.

The transport fingerprint is shown on the live status page for comparison.
These manually configured TCP/Backbone interfaces do not pin the remote identity.

## Connect a community or radio segment

An operator can use WD6 as an uplink for a network with its own participants.
[Contact WD6](mailto:abuse@wd6.net?subject=Reticulum%20community%20uplink) to
coordinate a fourteen-day trial. Share the software version, approximate link
bandwidth, network type and the services your participants intend to reach.
There is no need to share private identities, keys, participant addresses or logs.

For a radio segment with much less bandwidth than its Internet uplink, start
from [community.conf.example](community.conf.example): enable transport on your
own gateway, use `mode = boundary` for the WD6 uplink and `mode = internal` for
local interfaces that should resolve external destinations on demand. This
keeps wider-network announces off those internal interfaces while allowing
path requests when participants need a destination. Preserve the radio's actual
hardware and frequency configuration.

A same-speed IP transport connection can use `full` mode. Select modes for your
topology instead of applying the radio example universally. The WD6 public
listener already runs in `gateway` mode to resolve paths for connected clients.
[Official interface-mode documentation](https://reticulum.network/manual/interfaces.html#interface-modes)
explains how these modes affect announce propagation and recursive path requests.

Start with one WD6 connection. Retain your working network, and agree on a simple
rollback: disable the added interface and restore the previous interface modes.
Assess stable connected time, successful protocol/service transactions, route
contribution and radio queue/traffic pressure. Extra peer counts alone are not
evidence of useful connectivity.

## Troubleshooting and contact

- **TCP unreachable:** check DNS, Internet access and outbound TCP/4242, then live
  status. No VPN or Internet proxy service is provided by this endpoint.
- **RNS client disconnected:** check the interface name/type and profile used by
  the running shared instance. Avoid starting multiple daemons for the same profile.
- **TCP works but probes fail:** confirm that the interface is really running
  Reticulum; wait briefly for discovery and retry the protocol test. A TCP check
  is not enough to diagnose this case.
- **Repeated reconnects:** report the software/version and approximate interval.
  Include the check time and timezone; omit user traffic and raw peer addresses.

Community coordination, operational and abuse reports go to
[abuse@wd6.net](mailto:abuse@wd6.net). No operator LXMF contact is advertised until
we have verified its receiving and backup path.
