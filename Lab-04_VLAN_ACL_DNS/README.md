# Lab 04 - VLAN, DHCP, DNS, ACL Configuration

## 🧪 Lab Overview

This lab simulates a small business network with two VLANs (Staff and Guest), using DHCP and DNS services. An Access Control List (ACL) is implemented to restrict HTTP access from the Guest VLAN to the Staff VLAN and the internet. Only the Staff VLAN can access the simulated internet (via a DNS server).

---

## 🖥️ Network Topology

- **Router**: Cisco 2911  
- **Switch**: Cisco 2960  
- **4 PCs**:
  - **PC1 & PC2** → VLAN 10 (Staff)
  - **PC3 & PC4** → VLAN 20 (Guest)
- **1 Server** → Acts as DNS + “Internet” (VLAN 30, Static IP)

---

## 🔌 Connections

| Device | Port              | Connected To | Port            |
|--------|-------------------|--------------|-----------------|
| Router | GigabitEthernet0/0| Switch       | FastEthernet0/1 |
| Switch | FastEthernet1/1   | PC1          | FastEthernet0   |
| Switch | FastEthernet1/2   | PC2          | FastEthernet0   |
| Switch | FastEthernet1/3   | PC3          | FastEthernet0   |
| Switch | FastEthernet1/4   | PC4          | FastEthernet0   |
| Switch | FastEthernet1/5   | Server       | FastEthernet0   |

All connections use **Copper Straight-Through** cables.

---

## 📋 IP Scheme

| VLAN | Purpose | Subnet           | Gateway       | DHCP Range            |
|------|---------|------------------|---------------|------------------------|
| 10   | Staff   | 192.168.10.0/24  | 192.168.10.1  | 192.168.10.10–100      |
| 20   | Guest   | 192.168.20.0/24  | 192.168.20.1  | 192.168.20.10–100      |
| 30   | Server  | 192.168.30.0/24  | 192.168.30.1  | Static: 192.168.30.10  |

---

## 🎯 Objectives

- ✅ Create VLANs
- ✅ Configure trunking and access ports
- ✅ Set up subinterfaces on router
- ✅ Configure DHCP on router
- ✅ Assign static IP to DNS server
- ✅ Apply ACLs to restrict Guest access

---

## 🔒 ACL Rules

- Deny HTTP from Guest VLAN (192.168.20.0/24) to Staff VLAN (192.168.10.0/24) and Server.
- Permit all other traffic as needed.

---

## ✅ Test Commands

- `ping` between VLANs
- `ipconfig /renew` for DHCP
- Open web browser on PC to test HTTP restriction

