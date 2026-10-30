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
