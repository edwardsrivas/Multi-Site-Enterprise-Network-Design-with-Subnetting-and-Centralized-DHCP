**📡 Enterprise Multi-Site Network with Static Routing & Centralized DHCP**

<img width="516" height="560" alt="image" src="https://github.com/user-attachments/assets/87415ab2-2b0c-4330-ac5c-34013fb86cf5" />

**📌 Project Scope**

This project simulates the design, configuration, and validation of a multi-site enterprise network using Cisco networking concepts. The environment represents an organization with two geographically separated branch offices (GA and NY) and a centralized Data Center (DC) responsible for providing core network services.

The goal of the project was to enable secure, reliable communication between all sites, while centralizing IP address management (DHCP) in the Data Center. Rather than deploying individual DHCP servers at each branch, the network was designed to use DHCP relay, a common enterprise practice that simplifies management and improves scalability.

This lab was built from scratch in Cisco Packet Tracer, including:

- IP addressing design

- Subnet planning

- Router-to-router WAN connectivity

- Static routing

- Switch management configuration

- DHCP relay and scope validation

- End-to-end connectivity testing

**🏗️ Network Design Explanation**
**🧭 Multi-Site Topology**

The network consists of three main locations:

1. Georgia Branch Office (GA) – Contains end-user devices, a switch, and a router.

2. New York Branch Office (NY) – Similar setup to GA, demonstrating branch connectivity.

3. Central Data Center (DC) – Hosts centralized services including DHCP servers.

**📷 Topology Diagram**

Full Packet Tracer topology view

<img width="1893" height="666" alt="image" src="https://github.com/user-attachments/assets/623841be-646b-4004-89f5-58bf5794744a" />

This setup reflects a typical enterprise environment, where branch offices rely on centralized infrastructure for services like IP address management and inter-branch connectivity. The topology ensures that each site can communicate with all others, demonstrating both LAN and WAN interactions.

**📐 IP Addressing & Subnetting Strategy**

The first step in the lab is planning IP addressing for all sites. Proper subnetting ensures efficient use of IP space and avoids conflicts between branches.

**WAN Subnetting**

- /30 networks used for router-to-router links

- Ensures only two usable IPs per link

- Common in enterprise WAN designs

**LAN Subnetting**

- Branch LANs use /26 networks (up to 62 hosts)

- Data Center LAN uses a /24 network for servers and infrastructure

This approach demonstrates practical subnetting decisions, not arbitrary addressing.

**📷 Router Interface IPs**

New York Router

<img width="751" height="108" alt="image" src="https://github.com/user-attachments/assets/9055b305-48d1-4ee6-b615-8308c2bef8df" />

Georgia Router

<img width="720" height="104" alt="image" src="https://github.com/user-attachments/assets/d2683d52-d4b1-47a9-81f1-4b7ab33564b0" />

By carefully designing the subnets, this lab illustrates the importance of structured IP planning in enterprise networks and how it supports scalability and manageability.

**🛣️ Routing Implementation (Static Routing)**

After subnetting, static routes are configured on all routers to allow inter-site communication:

- Demonstrates understanding of packet forwarding logic

- Maintains full control over routing paths

- Reinforces foundational routing concepts

Routers do not rely on default routes — each network is explicitly defined.

**📷 Routing Table Verification**

Georgia Router

<img width="723" height="362" alt="image" src="https://github.com/user-attachments/assets/f4ca6947-e6a1-449a-b2a3-3a79dcf6483c" />

New York Router

<img width="718" height="363" alt="image" src="https://github.com/user-attachments/assets/27cad251-59a1-42df-829c-82d500d338bd" />

**🧠 Centralized DHCP Design**

Instead of deploying DHCP servers at each branch, all DHCP services are hosted in the Data Center. This design:

- Centralizes IP address management

- Simplifies administration

- Reflects real-world enterprise practices

Two DHCP servers were configured with static IPs:

- One handling GA scopes

- One handling NY scopes

**🔁 DHCP Relay (ip helper-address)**

Since DHCP requests are broadcast-based and cannot cross routers by default, DHCP relay was implemented on branch routers using ip helper-address.

When a client at a branch requests an IP:

1. The router intercepts the broadcast

2. Converts it to a unicast packet

3. Forwards it to the appropriate DHCP server in the DC

This allows remote clients to receive IP configuration from centralized servers.

📷 DHCP Relay Configuration

<img width="436" height="446" alt="image" src="https://github.com/user-attachments/assets/49c1a2be-dfaa-43bc-b446-3783fdd061c2" />


**🖥️ DHCP Scope & Client Validation**

End-user PCs at each branch were configured for DHCP and successfully received:

- IP address

- Subnet mask

- Default gateway

This confirms:

- DHCP relay functionality

- Routing correctness

- End-to-end connectivity

**📷 Client DHCP Assignment**

Georgia PC

<img width="943" height="504" alt="image" src="https://github.com/user-attachments/assets/a31e65f7-6d00-4261-a5e5-2a515bea6883" />

New York PC

<img width="940" height="502" alt="image" src="https://github.com/user-attachments/assets/66f849cd-ef33-4357-b78d-800ecbd18adf" />

**🔌 Switching & Management**

All switches were configured with:

- Management IP addresses on VLAN 1

- Default gateways pointing to local routers

- Spanning Tree Protocol (PVST) enabled

This allows remote management and reflects standard access-layer switch configuration.


**📸 Switch Management Config**

Georgia Switch

<img width="759" height="514" alt="image" src="https://github.com/user-attachments/assets/6c69faeb-73f9-412e-bab7-a1294bafb309" />

New York Switch

<img width="728" height="510" alt="image" src="https://github.com/user-attachments/assets/db1a0414-240f-4d0d-b9ef-339287b84f65" />

**✅ Testing & Verification**

Finally, the lab includes verification to confirm proper network operation:

1. Ping tests across all subnets verify routing is functional.

2. DHCP leases confirm clients are receiving addresses from the centralized servers.

3. Switch management IPs confirm accessibility for administrative tasks.

**📷 End-to-End Ping Test**

NY-PC -> GA-PC

<img width="544" height="382" alt="image" src="https://github.com/user-attachments/assets/c504c3f7-c475-47de-bdae-e746346d1bd3" />

**Key Concepts Demonstrated**
- Subnet planning and IP addressing
- Static routing between multiple sites
- Centralized DHCP with DCHP relay
- Enterprise switch configuration and management
- End-to-end network verification

This lab provides practical experience with enterprise network design, highlighting both the planning and configuration aspects required to build a functional, scalable, and manageable multi-site network.
