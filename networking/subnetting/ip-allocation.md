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