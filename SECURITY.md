# Responsible Lab Use

This project documents an isolated pfSense, Windows and Kali lab. Perform network testing only on systems you own or have explicit authorization to assess.

High-rate SYN traffic can disrupt services. Do not run high-rate traffic generation on public, shared or production networks. Safe firewall-rule validation can use bounded low-rate requests and correlated pfSense filter logs.

Do not commit credentials, private keys, pfSense configuration backups, VPN secrets or unredacted sensitive data. Restrict admin access with strong authentication, HTTPS and least privilege.

A failed ping, an unanswered SYN probe, or retransmissions alone do not prove a firewall blocked traffic or that a DoS succeeded.

## Publishing and access hardening

Public GitHub documentation does not control the pfSense appliance's network accessibility. Before publicly sharing current lab infrastructure, verify:

- No unnecessary WAN/NAT/host-router port forwards to pfSense GUI, SSH, OpenVPN, Snort management or other services.
- GUI access restricted to an authorized management interface and trusted hosts; use HTTPS with a valid certificate and strong authentication.
- OpenVPN server rules limited to approved remote users and authorized internal subnets; disable unused VPN profiles and rotate exposed credentials.
- Block unnecessary inter-VLAN access and check pass rules are not overly broad. Validate Guest restriction using the protocol actually specified by the rule.
- Keep pfSense packages, IDS signatures and operating systems patched. Review logs and active states after changes.
- Never include student identifiers, personal contact information, live public IPs, API tokens, passwords, certificate private keys, exported VPN profiles, or personal authentication data in the repository.

**Historical exposure:** If a sensitive identifier was already published in a commit or an image, replacing the current file does not automatically erase the old Git history or any cached copies. Review previous commits; for serious exposure, rotate affected secrets and follow GitHub's sensitive-data removal guidance.
