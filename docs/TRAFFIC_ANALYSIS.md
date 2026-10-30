# Traffic investigation — build, test, defend

## Windows endpoint
Screenshot shows `10.1.1.100/24` with gateway `10.1.1.1`. A ping to pfSense WAN `192.168.177.131` produced **4 successful replies**, confirming reachability during that test.

## Kali probe observations
One screenshot shows failed ICMP probes to `10.1.1.100` and `192.168.177.131`. Later a ping to the latter address succeeded with **11 of 11** responses. The snapshots document different outcomes at different times, without isolating their causes.

## Controlled high-rate SYN traffic
A Kali screenshot documents high-rate TCP SYN transmission directed to `10.1.1.100:80`, with no replies reported. This was an isolated authorized lab test, not evidence of successful denial of service. Do not recreate high-rate traffic on shared networks.

## Wireshark
Captured packets show repeated TCP **SYN retransmissions** involving `10.1.1.1` and `10.1.1.100` on TCP/80. Retransmissions can have several causes; the screenshot alone does not demonstrate which firewall rule matched.

## Analyst validation sequence
1. Record source, destination, protocol, port and timestamp.
2. Confirm interface direction and gateway routes.
3. Check a relevant firewall filter log entry and rule counter.
4. Review TCP state, destination service availability and host firewall.
5. Correlate packet captures and pfSense event timestamps.
6. Report what was observed separately from inferred causes.

**Conclusion:** The evidence supports network segmentation and traffic analysis practice, but does not independently prove a successful DoS or a specific mitigation response.
