
flowchart TB
    Internet((Internet))
    Remote[Remote Employees]
    VPN[VPN Gateway]
    FW[Edge Router / Firewall]
    Core[Core Layer 3 Switch]

    Internet --> FW
    Remote --> VPN
    VPN --> FW
    FW --> Core

    Core --> VLAN10["VLAN 10 - Development<br/>192.168.10.0/25"]
    Core --> VLAN20["VLAN 20 - SOC & IT<br/>192.168.10.128/26"]
    Core --> VLAN30["VLAN 30 - HR & Finance<br/>192.168.10.192/26"]
    Core --> VLAN40["VLAN 40 - Reception<br/>192.168.11.0/27"]
    Core --> VLAN50["VLAN 50 - Server Room<br/>192.168.11.32/27"]

    VLAN50 --> Servers[Internal Servers<br/>12 Current Devices]

    classDef security fill:#fce4d6,stroke:#c65911,color:#000
    classDef network fill:#d9eaf7,stroke:#2874a6,color:#000
    classDef server fill:#e2f0d9,stroke:#548235,color:#000

    class FW,VPN security
    class Core,VLAN10,VLAN20,VLAN30,VLAN40 network
    class VLAN50,Servers server






## Network Architecture Explanation

### 1. Internet Connection
Provides external network connectivity to the office.

### 2. Edge Router / Firewall
Connects the internal network to the internet
and filters unauthorized network traffic.

### 3. VPN Gateway
Provides secure remote access to authorized
employees working outside the office.

### 4. Core Layer 3 Switch
Connects departmental networks and handles
inter-VLAN routing according to security policies.

### 5. Departmental VLANs
Each department has a separate VLAN and subnet
to reduce unnecessary communication between
departments.

### 6. Server Room
Internal servers are placed in a separate VLAN
to restrict access to important company resources.

## Network Segmentation

| VLAN | Department | Network |
|---|---|---|
| 10 | Development | 192.168.10.0/25 |
| 20 | SOC & IT | 192.168.10.128/26 |
| 30 | HR & Finance | 192.168.10.192/26 |
| 40 | Reception | 192.168.11.0/27 |
| 50 | Server Room | 192.168.11.32/27 |