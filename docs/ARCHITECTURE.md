# Services and addressing

The report documents an Ubuntu-based teaching network. Apache serves local web pages; BIND9 handles local name resolution; DHCP assigns client addresses; hostapd provides wireless association; routing and NAT connect the client network to an uplink.

| Component | Historical configuration | Evidence |
| --- | --- | --- |
| Apache | Two virtual hosts with separate document roots; Basic authentication for a subdirectory | E013-E027 |
| BIND9 | Forward zones for two lab hostnames, aliases, and reverse-zone configuration | E037-E049 |
| ISC DHCP | Pool 192.168.18.100-200; reservations .10 and .20; DNS option .20 | E053 |
| Wireless AP | wlan0, nl80211 driver, WPA2-PSK/CCMP settings | E058, E067 |
| Wireless DHCP | dnsmasq bound to wlan0; pool 192.168.18.50-150; router option .1 | E072 |
| Routing | IPv4 forwarding and multiple NAT/FORWARD rule snapshots | E073-E080, E091-E092 |
| Monitoring | Shell scripts reading interface byte counters; performance logging and a systemd unit | E083-E090 |

Evidence IDs link through the [register](EVIDENCE.md). They are portfolio IDs, not original figure numbers.

## Configuration stages

The web and DNS screenshots use 192.168.18.10 and .20. A reverse query returns names for 10.0.2.15. The DHCP section contains both enp0s3 and enp0s8. Later wireless evidence includes wlan0, br0, and a route for 192.168.50.0/24 while other settings use 192.168.18.0/24.

These are historical configuration snapshots. They should not be combined into one configuration without reconciling interfaces, routes, service bindings, and subnets. ISC DHCP and dnsmasq are documented as separate setups; their overlapping pools are not presented as a safe concurrent configuration on one broadcast domain.

The historical .com hostnames are local lab labels. Their appearance in the screenshots does not imply ownership of those public domains.
