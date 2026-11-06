# Multi-Site Enterprise Network Architecture with OSPF & VLAN Segmentation

# 📌 Project Overview
This project demonstrates the design, deployment, and validation of a secure, multi-site enterprise network infrastructure using Cisco Packet Tracer. The architecture simulates a high-availability corporate communication link between a main Headquarters (HQ) and a regional branch office located in Abuja, Nigeria.

The design implements logical segmentation via **Virtual Local Area Networks (VLANs)**, **Inter-VLAN Routing (Router-on-a-Stick)**, and dynamic routing using **Open Shortest Path First (OSPFv2)** to ensure reliable end-to-end data delivery across disparate networks.

# ⚡ Core Technical Features
* **Logical Network Segmentation:** Implemented VLAN 10 (HR_Dept) and VLAN 20 (IT_Dept) on the local infrastructure to enhance corporate data security and minimize broadcast domains.
**Inter-VLAN Routing:** Configured a "Router-on-a-Stick" deployment via 802.1Q subinterfaces on the HQ gateway router, enabling controlled communication between local departments.
**Dynamic WAN Routing:** Deployed single-area OSPFv2 (Area 0) to share subnets dynamically between the HQ site and the Abuja site, automating topology updates and route determination.
**Scalable Architecture:** Built with proper subnetting principles, facilitating smooth horizontal scaling for future branch extensions or department additions.

# 🗺️ Network Topology Design & Addressing Schema

# 🏢 Headquarters (HQ) Site
**VLAN 10 (HR Department):** Subnet `192.168.10.0/24` | Default Gateway: `192.168.10.1`
**VLAN 20 (IT Department):** Subnet `192.168.20.0/24` | Default Gateway: `192.168.20.1`

# 🇳🇬 Abuja Branch Site
**Branch LAN:** Subnet `192.168.30.0/24` | Default Gateway: `192.168.30.1`

# 🌐 WAN Backbone (Inter-Router Link)
**Point-to-Point Link:** Subnet `10.0.0.0/30`
* `HQ-Router` IP: `10.0.0.1`
* `Abuja-Router` IP: `10.0.0.2`

# 📑 Implementation & Verification Screenshots

# 1. Functional Network Topology Map
![Network Topology](topology.png)
*Caption:* Fully converged multi-site topology highlighting visual link convergence and baseline connectivity between corporate endpoints and core infrastructure.

# 2. OSPF Dynamic Routing Table Convergence
![Control Plane Verification](Control%20Plane%20Verification.png)
*Caption:* Validation of the HQ Router routing table. Note the **"O" (OSPF)** flag prefix, proving successful dynamic routing protocol convergence to network `192.168.30.0/24` via the WAN interface.

# 3. End-to-End Control Plane Validation (ICMP Echo Request)
![Data plane Verification](Data%20plane%20Verification.png)
*Caption:* ICMP validation confirming end-to-end data delivery across multiple security zones and physical branches, proving accurate path allocation and zero routing loops.

# 🛠️ Key Commands Used for Verification
To inspect and troubleshoot this environment during operations, the following Cisco IOS command set was executed:
```text
HQ-Router# show interfaces trunk
HQ-Router# show ip interface brief
HQ-Router# show ip ospf neighbor
HQ-Router# show ip route
