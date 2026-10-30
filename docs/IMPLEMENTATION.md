# pfSense isolated homelab — implementation and verification

This guide describes the configuration visible in the original screenshots and provides a reproducible checklist. Steps not evidenced by a screenshot are identified as verification tasks, not completed facts.

## 1. Build VMware network segments

Use VMware Workstation with separate networks for **VMnet8 (NAT/WAN)**, **VMnet2 (Employee/host-only)** and **VMnet3 (Guest/host-only)**. Attach the pfSense WAN, EMPLOYEE and GUEST interfaces to the corresponding VMware virtual networks. Keep tests on authorized isolated systems.

The original network diagram uses a general home-router subnet, but the operational dashboard shows WAN **192.168.177.131**, Employee **10.1.1.1**, Guest **10.2.2.1**, and an online WAN gateway at **192.168.177.2**.

## 2. Complete setup and verify interfaces

Follow the pfSense setup wizard (screenshot confirms **Step 9 of 9 — completed**). In **Interfaces → Assignments**, validate NIC-to-network mappings, interface labels and addressing. In **Status → Dashboard**, verify link state and gateway health. The supplied dashboard shows all three network interfaces up on pfSense CE **2.8.1**.

## 3. Configure and verify DHCP

The dashboard confirms the **dhcpd** service is running. To fully document actual DHCP allocation, inspect **Services → DHCP Server** and **Status → DHCP Leases** (menu names can vary by version). Record which interface offers leases, its start/end pool, gateway/DNS values, and leases that match the correct subnet.

**Evidence limit:** The screenshots do not show the DHCP pool or any specific dynamic lease. The Employee Windows screenshot shows `10.1.1.100/24`, gateway `10.1.1.1`, but not whether this address was assigned by DHCP or configured statically.

## 4. Restrict administrator access

The screenshots show GUI access at **10.1.1.1** and an Employee anti-lockout rule. Review **System → Advanced → Admin Access**, require HTTPS with a trusted certificate, strong authentication, and restrict GUI/SSH exposure to an approved management system/subnet. Consider disabling SSH when not needed. The screenshots do not verify all of these hardening steps as already completed.

## 5. Configure firewall policy

Use **Firewall → Rules**. Rules are evaluated from top to bottom on the interface where traffic enters. The Guest screenshot shows **IPv4 TCP** deny Guest `10.2.2.0/24` → Employee `10.1.1.0/24` before general Guest allow. The Employee rule table also includes SSH, general traffic and ICMP allow rules.

Do not misreport visually disabled entries as enforced: **Social Media Block** and **Block HTTP from any** are disabled in the captured Employee rules.

Review policy-by-policy details in [FIREWALL_POLICIES.md](FIREWALL_POLICIES.md).

## 6. Record endpoint configuration and permitted paths

The Employee Windows screenshot captures `10.1.1.100/24` and default gateway `10.1.1.1`. It also captures four successful ICMP replies to pfSense WAN `192.168.177.131`. Document source, destination, interface, route and exact timestamp for each test.

## 7. Validate boundaries safely

Use bounded, low-rate connectivity and TCP connection checks on authorized endpoints. First establish an allowed baseline, then try a Guest-to-Employee **TCP** flow that matches the actual deny rule. Inspect packet captures, firewall logs and the matched rule/counter. A failed ping is not proof that the screenshot's TCP-only deny was involved.

## 8. Analyze recorded suspicious-looking traffic

The original Kali screenshot contains high-rate SYN packets directed at an isolated Windows VM on port 80. The packet captures show SYN retransmission behavior. Report this as **traffic-generation and observation evidence**, not as a successful DoS or proven firewall mitigation.

## 9. Check updates and maintenance

The pfSense update screen captures version **2.8.1**, status **Up to date** at the recorded time. The dashboard shows pfBlockerNG-related package status. Confirm that IP or DNSBL filtering is actually enforced before claiming blocked domains or addresses.

## 10. Record final disposition

Describe each test using the template: **Source → Destination → Protocol/port → Expected policy → Packet observation → Firewall decision evidence → Result → Follow-up**. Keep the build-test-defend loop reproducible without overstating the available evidence.
