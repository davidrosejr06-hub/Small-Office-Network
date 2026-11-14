# Small Office Network — Cisco Packet Tracer

## Project overview
Built a simulated small office LAN with four PCs, a Cisco 2960 switch, and a Cisco 1941 router. Configured static IPv4 addresses, tested connectivity, and practiced diagnosing incorrect IP addresses, subnet masks, and administratively disabled router interfaces.

## Objectives
- Build a small LAN and connect devices using Ethernet cables.
- Configure IPv4 addresses, subnet masks, and a default gateway.
- Verify local connectivity with `ping` and inspect settings with `ipconfig`.
- Diagnose common Layer 2/Layer 3 connectivity issues.

## Topology
- Router: Cisco 1941, GigabitEthernet0/0, `192.168.10.1/24`
- Switch: Cisco 2960
- PCs: four end devices connected to switch access ports

| Device | IPv4 address | Subnet mask | Default gateway |
|---|---|---|---|
| Router G0/0 | 192.168.10.1 | 255.255.255.0 | N/A |
| PC0 | 192.168.10.100 | 255.255.255.0 | 192.168.10.1 |
| PC1 | 192.168.10.101 | 255.255.255.0 | 192.168.10.1 |
| PC2 | 192.168.10.102 | 255.255.255.0 | 192.168.10.1 |
| PC3 | 192.168.10.103 | 255.255.255.0 | 192.168.10.1 |

## Tools and commands
- Cisco Packet Tracer
- PC commands: `ipconfig`, `ping`, `arp -a`
- Cisco IOS: `show ip interface brief`, `shutdown`, `no shutdown`, `copy running-config startup-config`

## Troubleshooting exercises

| Scenario | Introduced fault | Expected diagnosis | Fix | Observed result |
|---|---|---|---|---|
| 1 | PC2 changed to `192.168.20.102/24` | Incorrect subnet / unreachable configured gateway | Restore `192.168.10.102/24` | request timed out |
| 2 | PC1 changed to `192.168.10.101/26` | Gateway `.1` outside PC1's perceived `/26` subnet | Restore `/24` mask | 0% packet loss |
| 3 | Router G0/0 shut down | Interface administratively down | Issue `no shutdown` | request timed out |



## Validation evidence
Add screenshots under `screenshots/` showing:
1. Full Packet Tracer topology
2. Router `show ip interface brief` showing G0/0 up/up
3. Successful PC0-to-router ping
4. Successful PC0-to-PC1 ping
5. Optional before/after troubleshooting evidence

## What I learned
- Devices on the same subnet and VLAN can communicate through a switch without routing.
- A `/24` mask is `255.255.255.0`; a `/26` mask divides a /24 into four blocks of 64 addresses.
- A disabled router interface prevents access to the router while local switch traffic may still work.
- Connectivity tests should be recorded to distinguish a suspected cause from a verified fix.


