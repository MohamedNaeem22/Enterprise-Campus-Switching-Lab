# Enterprise Campus LAN Design & Switching Implementation (Cisco Packet Tracer)

A comprehensive multi-tier Enterprise Campus Switching project implemented in **Cisco Packet Tracer**, demonstrating core networking concepts, redundancy, high availability, and secure device administration.
<img width="1610" height="646" alt="switching task‏" src="https://github.com/user-attachments/assets/fdf1997d-e836-49d8-9af6-0b53cb638b28" />

---

## 📌 Project Architecture & Topology
The network is structured using Cisco's Hierarchical Campus Network Model:
- **Core Layer:** Cisco Catalyst 3560 Multilayer Switch (acts as Inter-VLAN router, VTP Server, and Spanning Tree Root Bridge).
- **Distribution Layer:** Redundant Cisco Catalyst Switches aggregating traffic with Link Aggregation (EtherChannel) to the core.
- **Access Layer:** Cisco Catalyst 2960 Switches delivering secure access to end devices (PCs, Laptops, and VoIP IP Phones).

---

## 🚀 Key Implemented Features

1. **VLAN Segmentation & IP Addressing:**
   - **VLAN 10 (Sales / Data 1):** `192.168.10.0/24` (Gateway: `192.168.10.1`)
   - **VLAN 20 (IT / Data 2):** `192.168.20.0/24` (Gateway: `192.168.20.1`)
   - **VLAN 30 (HR / Data 3):** `192.168.30.0/24` (Gateway: `192.168.30.1`)
   - **VLAN 40 (Voice Network):** `192.168.40.0/24` (Gateway: `192.168.40.1`)
2. **Inter-VLAN Routing & SVIs:**
   - Enabled `ip routing` on the Core MLS with Switch Virtual Interfaces (SVIs) as default gateways.
3. **EtherChannel (Link Aggregation):**
   - Configured Cisco PAgP/LACP bundles between Core and Distribution switches for aggregated bandwidth and failover redundancy.
4. **Spanning Tree Protocol (STP):**
   - Deterministic root bridge placement via `spanning-tree vlan ... root primary/secondary`.
   - Enabled `spanning-tree portfast` on edge access ports for immediate forwarding.
5. **VTP (VLAN Trunking Protocol):**
   - Centralized VLAN administration via VTP Server/Client architecture with domain and password authentication.
6. **Voice VLAN & Multi-VLAN Access Ports:**
   - Configured Cisco IP Phone access ports supporting dual tagging: untagged Data traffic (VLAN 10/20) and 802.1Q tagged Voice traffic (VLAN 40).
7. **Automated IP Allocation (DHCP Server):**
   - Centralized DHCP pools on the Core Switch with excluded management ranges and Option 150 for VoIP provisioning.
8. **Management Security (SSH & Console):**
   - Hardened Console with password authentication and synchronous logging.
   - Secure Remote Shell (SSHv2) with RSA 1024-bit encryption keys and privilege 15 administration.

---

## 🔐 Credentials & Device Access
For testing and verification in Cisco Packet Tracer:
- **Enable Secret Password:** `class`
- **Console Password:** `cisco`
- **SSH Credentials:**
  - **Username:** `admin`
  - **Password:** `cisco123`
- **VTP Domain:** `instant.local`
- **VTP Password:** `cisco`

---

## 🛠️ Verification & Testing
- ✅ **Inter-VLAN Connectivity:** Verified end-to-end ping reachability between distinct subnets.
- ✅ **EtherChannel Status:** Validated bundled active links via `show etherchannel summary`.
- ✅ **VTP & Trunking:** Confirmed dynamic VLAN propagation and 802.1Q encapsulation via `show interfaces trunk`.
- ✅ **DHCP Binding:** Successful dynamic IP assignment across all endpoints.

---
**Simulated in:** Cisco Packet Tracer  
**Author:** Mohamed Naeem
