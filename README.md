**📡 Enterprise Multi-Site Network with Static Routing & Centralized DHCP**

(Cisco Packet Tracer Project)

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

The network consists of three logical sites:

- GA (Georgia Branch Office)

- NY (New York Branch Office)

- DC (Data Center / Core Services)

Each branch contains:

- A router

- A switch

- End-user devices (PCs)

The Data Center contains:

- A core router

- A switch

Centralized DHCP servers for multiple sites

WAN connections between routers use /30 point-to-point networks to conserve IP address space and follow best practices.

**📷 Topology Diagram**

Full Packet Tracer topology view

<img width="1893" height="666" alt="image" src="https://github.com/user-attachments/assets/623841be-646b-4004-89f5-58bf5794744a" />

**📐 IP Addressing & Subnetting Strategy**

The IP addressing plan was carefully designed to:

- Separate each site into its own logical network

- Use different subnet sizes based on purpose

- Prevent IP overlap

- Support scalability

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

**🛣️ Routing Implementation (Static Routing)**

Static routing was intentionally chosen instead of a dynamic routing protocol to:

- Demonstrate understanding of packet forwarding logic

- Maintain full control over routing paths

- Reinforce foundational routing concepts

Each router was configured with static routes to all remote LAN networks, ensuring full inter-site communication.

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

Connectivity was verified using:

Ping tests between PCs across sites

Router-to-router reachability tests

DHCP lease validation

**📷 End-to-End Ping Test**

NY-PC -> GA-PC

<img width="544" height="382" alt="image" src="https://github.com/user-attachments/assets/c504c3f7-c475-47de-bdae-e746346d1bd3" />
