# Firewall policy review

## Observed topology
- pfSense WAN: `192.168.177.131` (VMnet8 NAT), gateway `192.168.177.2`.
- EMPLOYEE: `10.1.1.1/24` (VMnet2).
- GUEST: `10.2.2.1/24` (VMnet3).

## Guest firewall rules (original screenshot)

1. **Block Internal VLANs** — deny **IPv4 TCP** traffic from `10.2.2.0/24` to `10.1.1.0/24`.
2. **Block SSH Access** — deny TCP destination port **22**, destination displayed as `192.168.177.131/24`; confirm the intended address/mask because /24 is broader than one host.
3. **Allow to Internet** — pass for Guest subnets to **any**. Its label does not itself restrict destinations only to the Internet.

Rule order is important: pfSense evaluates interface policy top-down. A TCP-only deny does not establish an ICMP restriction. Attribute drops only using relevant pfSense rule counters and filter logs.

## Employee interface

Captured entries include anti-lockout, pfBlockerNG IP/DNSBL-related entries, an allow-SSH rule, an Employee-subnets pass, and an ICMP pass. The entries labelled **Social Media Block** and **Block HTTP from any** are visibly **disabled**, so they cannot be claimed as enforced.

## Practical validation
Compare interface, source/destination, protocol/port, firewall rule ID and the log decision. Use bounded, authorized traffic to test the exact rule. Distinguish management-plane rules from ordinary user traffic.
