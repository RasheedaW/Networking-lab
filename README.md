# 📡 VLAN & Inter-VLAN Routing Lab (Cisco Packet Tracer)

This lab demonstrates how to segment a network using VLANs and enable communication between them using **Inter-VLAN Routing** via subinterfaces on a router.

---

## 🧰 Tools Used

- Cisco Packet Tracer
- 2960 Switch
- 2911 Router
- 2 End Devices (PCs)

---

## 🖥️ Network Design

| VLAN | Name  | IP Range         | Default Gateway   |
|------|-------|------------------|-------------------|
| 10   | Sales | 192.168.10.0/24  | 192.168.10.1      |
| 20   | HR    | 192.168.20.0/24  | 192.168.20.1      |

---

## Router Configuration (Router-on-a-Stick)

```bash
enable
configure terminal

interface g0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0

interface g0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0

interface g0/0
 no shutdown
exit

## Switch Configuration
enable
configure terminal

vlan 10
 name Sales
vlan 20
 name HR

interface range fa0/1 - 10
 switchport mode access
 switchport access vlan 10

interface range fa0/11 - 20
 switchport mode access
 switchport access vlan 20

interface fa0/24
 switchport trunk encapsulation dot1q
 switchport mode trunk
exit
 
Ping Test Results
From HR-PC (VLAN 20) to SALES-PC (VLAN 10):
C:\> ping 192.168.10.10

Reply from 192.168.10.10: bytes=32 time<1ms TTL=127
Reply from 192.168.10.10: bytes=32 time<1ms TTL=127
Reply from 192.168.10.10: bytes=32 time<1ms TTL=127

From Sales-PC (VLAN 10) to HR-PC (VLAN 20):
C:\> ping 192.168.20.10

Reply from 192.168.20.10: bytes=32 time<1ms TTL=255
Reply from 192.168.20.10: bytes=32 time<1ms TTL=255
Reply from 192.168.20.10: bytes=32 time<1ms TTL=255




