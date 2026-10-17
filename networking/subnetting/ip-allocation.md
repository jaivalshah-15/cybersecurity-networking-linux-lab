# IPv4 Subnetting and IP Allocation Plan

## 1. Network Overview

The company has been assigned the following private IPv4 network:

- Network Address: 192.168.10.0
- CIDR Prefix: /24
- Subnet Mask: 255.255.255.0
- Total IP Addresses: 256
- Usable Host Addresses: 254

## 2. Device Capacity Calculation

The company requires an additional 20% capacity for future expansion.

Formula:

Required Capacity = Current Devices × 1.20

| Department | Current Devices | Required Capacity |
|---|---:|---:|
| Reception & Administration | 20 | 24 |
| HR & Finance | 35 | 42 |
| Development Team | 60 | 72 |
| SOC & IT Operations | 45 | 54 |
| Server Room | 12 | 15 |
| **Total** | **172** | **207** |

Note: Infrastructure devices such as routers, switches
and access points will also require IP addresses.
Their exact additional quantity must be confirmed
during detailed network implementation.

## 3. Minimum Subnet Requirements

The number of usable hosts is calculated using:

Usable Hosts = 2^h - 2

Where h represents the number of host bits.

| Department | Required Hosts | CIDR | Subnet Mask | Usable Hosts |
|---|---:|---:|---|---:|
| Development | 72 | /25 | 255.255.255.128 | 126 |
| HR & Finance | 42 | /26 | 255.255.255.192 | 62 |
| SOC & IT Operations | 54 | /26 | 255.255.255.192 | 62 |
| Reception & Administration | 24 | /27 | 255.255.255.224 | 30 |
| Server Room | 15 | /27 | 255.255.255.224 | 30 |

These are minimum subnet sizes based on the
calculated departmental requirements, before
accounting for additional infrastructure addresses.






## 4. VLSM IP Address Allocation

The original /24 network is insufficient.
Therefore, the proposed alternative is 192.168.10.0/23.

The subnets are allocated from largest to smallest.

| Department | Network Address/CIDR | Subnet Mask | First Usable IP | Last Usable IP | Broadcast Address | Usable Hosts |
|---|---|---|---|---|---|---:|
| Development | 192.168.10.0/25 | 255.255.255.128 | 192.168.10.1 | 192.168.10.126 | 192.168.10.127 | 126 |
| SOC & IT Operations | 192.168.10.128/26 | 255.255.255.192 | 192.168.10.129 | 192.168.10.190 | 192.168.10.191 | 62 |
| HR & Finance | 192.168.10.192/26 | 255.255.255.192 | 192.168.10.193 | 192.168.10.254 | 192.168.10.255 | 62 |
| Reception & Administration | 192.168.11.0/27 | 255.255.255.224 | 192.168.11.1 | 192.168.11.30 | 192.168.11.31 | 30 |
| Server Room | 192.168.11.32/27 | 255.255.255.224 | 192.168.11.33 | 192.168.11.62 | 192.168.11.63 | 30 |

## 5. Allocation Verification

- All five subnets are non-overlapping.
- All five subnets fit within 192.168.10.0/23.
- The allocation provides 310 usable host addresses.
- 207 addresses are required for the calculated departmental capacity.
- Remaining usable capacity: 103 addresses.

The remaining capacity can accommodate network infrastructure
and future expansion, subject to detailed planning.

## 6. Gateway Allocation

For this proposed design, the first usable IP address
of each subnet is reserved as its default gateway.

The gateway can be configured on the appropriate
router interface or Layer 3 switch interface.







## 7. Network Capacity Analysis

### Q4.1 Original Network Capacity

The assigned network is 192.168.10.0/24.

Total IP addresses = 2^8 = 256

Usable IP addresses = 256 - 2 = 254

### Q4.2 Network Sufficiency

The five required subnet blocks are:

- Development: 128 addresses
- SOC & IT Operations: 64 addresses
- HR & Finance: 64 addresses
- Reception & Administration: 32 addresses
- Server Room: 32 addresses

Total required address space = 320 addresses.

The original /24 network provides only 256 addresses.
Therefore, it is insufficient.

### Q4.3 Recommended Alternative

I recommend requesting an expanded network
of 192.168.10.0/23.

This provides:

- Total addresses: 512
- Usable addresses: 510
- Address range: 192.168.10.0 to 192.168.11.255

This alternative supports the proposed departmental
subnets and provides room for future expansion.

### Q4.4 Importance of Future Planning

Future planning helps organizations accommodate
additional employees, computers, servers and network
devices without frequently redesigning their networks.

It also improves scalability, network management
and resource allocation.