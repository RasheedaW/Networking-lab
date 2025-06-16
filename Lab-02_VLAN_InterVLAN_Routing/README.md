# Lab 02 - VLAN and Inter-VLAN Routing Setup

## Objective
Configure VLANs on switches, set up router-on-a-stick inter-VLAN routing, and verify connectivity between VLANs using Cisco Packet Tracer.

## Lab Setup
- 2 Switches (Cisco 2960)
- 1 Router (Cisco 2811)
- 4 PCs (2 PCs per VLAN)

## Steps
1. Create VLAN 10 and VLAN 20 on both switches.
2. Assign switch ports (e.g., Fa0/1 & Fa0/2 to VLAN 10, Fa0/3 & Fa0/4 to VLAN 20).
3. Configure trunk ports between switches (Fa0/24) and between Switch1 and router (Fa0/23).
4. Configure router subinterfaces with dot1Q encapsulation for VLAN 10 and VLAN 20 with IPs 192.168.10.1 and 192.168.20.1.
5. Assign IP addresses on PCs matching VLAN subnets (e.g., 192.168.10.10, 192.168.20.10).
6. Test connectivity: ping router subinterfaces and between PCs.
7. Troubleshoot any connectivity issues.

## Key Learnings
- VLAN creation and port assignment  
- Trunk port configuration  
- Router-on-a-stick inter-VLAN routing concept  
- Basic network troubleshooting commands

## Troubleshooting Tips
- `show vlan brief` — verify VLAN assignments  
- `show interfaces trunk` — check trunk ports  
- `show ip interface brief` — verify router subinterfaces  
- Check PC IP and gateway configurations

## Files
- VLAN-InterVLAN-Routing-Lab.pkt (Packet Tracer topology)  
- RouterConfig.txt (Router configuration commands)  
- SwitchConfig.txt (Switch configuration commands)
