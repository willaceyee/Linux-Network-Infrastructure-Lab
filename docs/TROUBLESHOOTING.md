# Troubleshooting and evidence limits

## Wireless clients associated but lacked connectivity

The report describes clients joining the AP but failing to reach the uplink. It records adding forwarding rules between wlan0 and br0 and saving them through netfilter-persistent (E091-E092). This illustrates the need to check routing, forwarding policy, and NAT together. The snippets alone do not prove a final working end-to-end network.

The narrative reports successful outbound DNS/HTTPS traffic despite a phone displaying No Internet. A packet capture is mentioned, but no supporting capture file or corresponding packet screenshot was supplied. That outcome is retained as a reported observation, not a newly verified result.

## Interface and subnet changes

E064 shows Netplan settings, E065 shows a bridge, and E078 shows a routing table. Interface roles and client subnets vary across these snapshots. Before recreating the environment, establish the actual uplink, LAN, wireless interface, and gateway. The report does not show a complete final bridge configuration.

## DNS checks cover different address stages

E037-E046 show LAN zone configuration, while E049 queries 10.0.2.15. The reverse query returned two PTR answers with NOERROR. This does not establish that all forward and reverse mappings for the final 192.168.18.0/24 network were tested.

## DHCP evidence has distinct strengths

E055 shows a lease file without active lease entries. E056 shows client DHCP OFFER, REQUEST, and ACK messages, providing stronger evidence of an actual exchange. E053 shows default-lease-time 18000 and max-lease-time 36000 seconds: the default is not a guaranteed minimum. The narrative contains a conflicting 30000-second value.

## Monitoring service path mismatch

E087 refers to /usr/local/bin/performance_monitor.sh, while the unit in E089 uses /root/performance_monitor.sh. These paths must agree before startup can be reliable. E090 shows enable/start commands; it does not show successful monitor-service status or a crash-recovery test. Enabling a service at boot also does not itself configure automatic restart after failure.

## Firewall claims need policy evidence

The shown INPUT rules allow selected traffic, but no complete ruleset or default-drop policy is demonstrated. They do not prove that every other port is blocked. NAT translates addresses; it does not replace an explicit filtering policy. The additional-features screenshot alone also does not demonstrate a complete DNS policy, including TCP DNS.

## Web security and capacity

The screenshots show Basic authentication configuration, not an authenticated-browser success and failure sequence. Basic credentials require TLS for transport protection; the historical HTTP setup is a lab example. The prefork configuration screenshot is not evidence of a concurrent-user performance test.

## What has been verified here

Portfolio checks cover image provenance, redaction, file integrity, and documentation links. They do not certify the original system, reproduce the 2025 lab, or establish production readiness.
