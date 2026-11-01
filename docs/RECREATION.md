# Lab recreation checklist

The original Ubuntu VM and configuration files were not supplied as independent runnable artifacts. This checklist describes the work needed to recreate and validate the documented lab; it is not a tested installer.

1. Use an isolated Ubuntu VM or lab machine. Record its release, interface names, and network adapters. Wireless AP functionality requires a compatible adapter with AP-mode support and access from the guest if virtualized.
2. Choose one consistent LAN subnet, gateway, DHCP pool, reservations, and DNS address. Reconcile the historical address changes before applying settings.
3. Configure Apache virtual hosts and test both Host names. Test directory authentication with valid and invalid credentials. Use TLS if credentials leave an isolated training environment.
4. Configure DNS forward, alias, and reverse records. Validate syntax and test each expected record against the intended server, including reverse lookups for the chosen LAN addresses.
5. Choose which DHCP service serves each interface. Avoid competing DHCP servers and overlapping pools on a shared broadcast domain. Verify a client lease, advertised DNS, router option, and reservation.
6. Configure hostapd with a new private passphrase. Bind wireless DHCP to the correct client interface. Confirm association and client addressing.
7. Verify routes, IPv4 forwarding, NAT, and both directions of the forwarding policy. Test client DNS and local HTTP before outbound connectivity.
8. Reconcile monitoring script paths and systemd ExecStart. Verify service status, logs, expected output, reboot behavior, and any configured failure recovery.
9. Back up the actual configuration and record a full final ruleset and addressing table. Capture fresh client results to close the historical evidence gaps listed in [troubleshooting](TROUBLESHOOTING.md).

No networking commands from the report have been applied to the host computer during portfolio preparation.
