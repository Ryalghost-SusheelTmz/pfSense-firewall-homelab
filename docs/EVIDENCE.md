# Original screenshot evidence index

All images are original files supplied for this project and should be uploaded into `assets/evidence/`, using these filenames. Each README section references the corresponding file.

| Filename | Evidence |
|---|---|
| 01-home-lab-network-architecture.png | VMware/pfSense network design |
| 02-pfsense-setup-complete.png | Successful pfSense setup wizard |
| 03-pfsense-dashboard.png | Actual pfSense interface IPs, gateways and services |
| 04-employee-firewall-rules.png | Employee interface rule states |
| 05-guest-firewall-rules.png | Guest TCP deny/allow rules |
| 06-windows-connectivity.png | Windows addressing and successful ping |
| 07-kali-connectivity-tests.png | Kali ping tests; different results over time |
| 08-kali-syn-traffic.png | Authorized high-rate SYN test in isolated VM |
| 09-wireshark-syn-retransmissions.png | Captured TCP SYN retransmission |
| 10-wireshark-and-pfsense.png | Wireshark and firewall dashboard side by side |
| 11-pfsense-version-status.png | Software version and update status |

**Evidence interpretation:** The network drawing is a design, not proof of every deployed interface. Use the live pfSense dashboard for deployed addresses. No image alone establishes that the high-rate SYN traffic caused a denial of service or that a particular firewall rule blocked it. Review images for sensitive information before publishing.

## Additional VPN and Snort IDS evidence (privacy-redacted upload set)

The following are **original user-provided screenshots** organized as files 12–18. Student number regions have been obscured in images 16 and 17 before publication. Their GitHub references will display once the sanitized files are uploaded.

| Filename | Evidence |
|---|---|
| 12-pfsense-vm-console.png | pfSense console with server, management, Employee/Guest and VLAN addressing |
| 13-interface-assignments-and-vlans.png | Interface-to-NIC and VLAN mapping |
| 14-openvpn-server-profiles.png | OpenVPN contractor and remote-user server profiles |
| 15-openvpn-client-connected.png | Windows client tunnel status, connection logs and VPN IP |
| 16-snort-ssh-detection.png | Local SSH connection monitoring alert; student number covered |
| 17-snort-http-domain-alerts.png | HTTP policy and protocol anomaly alerts; student number covered |
| 18-snort-large-http-upload.png | Local HTTP POST upload-size monitoring alert |

**Security disclosure caution:** This repository is public. Publishing sanitized screenshots cannot close or conceal a reachable firewall/VPN service. To reduce exposure, evaluate WAN and upstream router port forwarding, GUI/SSH/OpenVPN access controls, credentials, and live logs in pfSense. Private RFC1918 IP addresses shown in the screenshots are not by themselves routable from the public Internet. Avoid posting private keys, downloadable VPN client configurations, live public IPs and account secrets.
