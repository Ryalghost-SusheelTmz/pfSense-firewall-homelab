# Responsible Lab Use

This project documents an isolated pfSense, Windows and Kali lab. Perform network testing only on systems you own or have explicit authorization to assess.

High-rate SYN traffic can disrupt services. Do not run high-rate traffic generation on public, shared or production networks. Safe firewall-rule validation can use bounded low-rate requests and correlated pfSense filter logs.

Do not commit credentials, private keys, pfSense configuration backups, VPN secrets or unredacted sensitive data. Restrict admin access with strong authentication, HTTPS and least privilege.

A failed ping, an unanswered SYN probe, or retransmissions alone do not prove a firewall blocked traffic or that a DoS succeeded.
