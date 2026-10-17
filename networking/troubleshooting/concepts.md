# Networking Concepts and Troubleshooting

## Q1. Private IP Address vs Public IP Address

An IP (Internet Protocol) address is a logical address assigned to a device to identify it and enable communication over a network.

### Private IP Address

A private IP address is used within local networks such as home, college, and office networks. It is not directly routable over the public internet.

The three private IPv4 address ranges are:

- 10.0.0.0/8
- 172.16.0.0/12
- 192.168.0.0/16

Example: 192.168.1.10

### Public IP Address

A public IP address is globally routable and is used for communication over the internet. It is generally assigned by an Internet Service Provider (ISP).

### Differences

| Private IP | Public IP |
|---|---|
| Used in local networks | Used on the internet |
| Not directly routable over the public internet | Globally routable |
| Can be reused in different private networks | Must be globally unique at a given time |
| Commonly assigned by a local router | Commonly assigned by an ISP |

### NAT (Network Address Translation)

NAT allows devices with private IP addresses to access the internet by translating their private addresses into a public IP address at the router.

For example, multiple computers in an office can access the internet through one public IP address using NAT.

### Conclusion

Private IP addresses are used for communication within local networks, whereas public IP addresses enable communication over the internet. NAT helps private networks communicate with the public internet.









## Q2. Subnetting

Subnetting is the process of dividing a large network into smaller networks called subnets. Each subnet has its own network address and IP address range.

### Why Organizations Use Subnetting

1. **Better Security:** Different departments can be separated, and unnecessary communication can be restricted.
2. **Reduced Network Traffic:** Subnetting reduces unnecessary broadcast traffic within each subnet.
3. **Easy Management:** It makes network administration and troubleshooting easier.
4. **Efficient IP Allocation:** IP addresses can be allocated according to the requirements of each department.
5. **Improved Network Organization:** Devices can be grouped according to departments or functions.

### Practical Example

Consider an organization using the network 192.168.1.0/24. It can be divided into four smaller /26 subnets.

| Subnet | Network Address | Usable Host Range | Broadcast Address |
|---|---|---|---|
| 1 | 192.168.1.0/26 | 192.168.1.1 – 192.168.1.62 | 192.168.1.63 |
| 2 | 192.168.1.64/26 | 192.168.1.65 – 192.168.1.126 | 192.168.1.127 |
| 3 | 192.168.1.128/26 | 192.168.1.129 – 192.168.1.190 | 192.168.1.191 |
| 4 | 192.168.1.192/26 | 192.168.1.193 – 192.168.1.254 | 192.168.1.255 |

Each subnet contains 64 total addresses and 62 usable host addresses.

### Conclusion

Subnetting helps organizations divide large networks into smaller, manageable networks. It improves organization, security, and efficient IP address management.












## Q3. Default Gateway

A default gateway is a networking device, usually a router, that forwards data from a local network to other networks, including the internet.

### Practical Example

Consider a computer with the following network configuration:

- IP Address: 192.168.1.25
- Subnet Mask: 255.255.255.0
- Default Gateway: 192.168.1.1

When the computer wants to communicate with a device outside its local network, it sends the data to the default gateway (192.168.1.1). The router then forwards the data towards the destination network.

### What Happens If the Default Gateway Is Incorrect?

1. The computer may still communicate with devices in its local network.
2. It may not be able to access the internet.
3. Communication with devices on other networks may fail.

### Conclusion

A default gateway connects a local network to other networks. It allows computers to communicate with devices outside their own subnet.







## Q4. DNS (Domain Name System)

DNS stands for Domain Name System. It translates human-readable domain names into IP addresses so that computers can locate servers on a network.

For example, when a user enters google.com in a browser, DNS helps find the IP address associated with that domain name.

### How DNS Works

1. The user enters a domain name in the browser.
2. The browser checks available cached DNS information.
3. If necessary, a DNS query is sent to a DNS resolver.
4. The resolver finds the corresponding IP address.
5. The browser uses that IP address to connect to the website.

### DNS Troubleshooting Scenario

If a user can access a website using its IP address but cannot access it using its domain name, the problem may be related to DNS resolution.

### Possible Causes

1. Incorrect DNS server configuration.
2. DNS server is unavailable.
3. Network problems affecting DNS requests.
4. Incorrect or outdated DNS records.
5. DNS cache problems.

### Commands Used for DNS Troubleshooting

| Command | Purpose |
|---|---|
| ping 8.8.8.8 | Tests connectivity to an external IP address. |
| ping google.com | Tests connectivity using a domain name. |
| nslookup google.com | Checks DNS resolution. |
| ip route | Displays routing information. |

### Conclusion

DNS makes internet browsing easier by translating domain names into IP addresses. DNS troubleshooting helps identify problems that prevent users from accessing websites through their domain names.












## Q5. DHCP (Dynamic Host Configuration Protocol)

DHCP stands for Dynamic Host Configuration Protocol. It automatically assigns network configuration to devices connected to a network.

DHCP provides the following information:

- IP address
- Subnet mask
- Default gateway
- DNS server address

### Working of DHCP (DORA Process)

DHCP follows four steps known as DORA:

1. **Discover:** The client searches for an available DHCP server.
2. **Offer:** The DHCP server offers an available IP address.
3. **Request:** The client requests the offered IP address.
4. **Acknowledge:** The server confirms the IP address assignment.

### Problems When a Client Cannot Obtain an IP Address

1. DHCP server is unavailable.
2. DHCP service is not running.
3. The DHCP address pool is exhausted.
4. Network cable or Wi-Fi connectivity problems.
5. Firewall or network configuration blocks DHCP requests.

When a device cannot obtain an IPv4 address from a DHCP server, it may automatically assign itself an APIPA address in the 169.254.0.0/16 range.

### Commands for Network Configuration

| Command | Purpose |
|---|---|
| ip addr | Displays network interfaces and assigned IP addresses. |
| ip route | Displays routing information and the default gateway. |
| nmcli device status | Displays the status of network devices. |

### Conclusion

DHCP simplifies network administration by automatically assigning IP addresses and other network settings to devices. It reduces manual configuration and helps prevent IP address conflicts.









## Q6. TCP vs UDP

TCP stands for Transmission Control Protocol, while UDP stands for User Datagram Protocol. Both are transport-layer protocols used for communication between devices.

### TCP (Transmission Control Protocol)

TCP is a connection-oriented protocol that establishes a connection before transferring data.

Features:
- Provides reliable data delivery.
- Uses acknowledgements.
- Retransmits lost data.
- Maintains the correct order of data.
- Performs error checking.

Practical examples:
- Downloading files.
- Sending emails.
- Loading websites using HTTPS.

### UDP (User Datagram Protocol)

UDP is a connectionless protocol that sends data without establishing a connection or guaranteeing delivery.

Features:
- Has lower communication overhead.
- Does not guarantee delivery.
- Does not provide built-in retransmission.
- Does not guarantee packet order.
- Is useful for real-time communication.

Practical examples:
- Online gaming.
- Live video streaming.
- Voice and video calls.

### Differences Between TCP and UDP

| TCP | UDP |
|---|---|
| Connection-oriented | Connectionless |
| Reliable data delivery | Delivery is not guaranteed |
| Uses acknowledgements | No transport-level acknowledgements |
| Retransmits lost data | No built-in retransmission |
| Maintains data order | Does not guarantee order |
| More overhead | Less overhead |
| Used by HTTPS and email | Used by DNS, gaming and VoIP |

### Conclusion

TCP is suitable when reliable and ordered data delivery is important. UDP is suitable when low latency and reduced communication overhead are more important than guaranteed delivery.









## Q7. VPN (Virtual Private Network)

VPN stands for Virtual Private Network. It creates an encrypted connection between a user's device and a remote network over the internet.

A VPN allows remote employees to securely access their organization's internal resources while working from home or travelling.

### How a VPN Works

1. The employee connects their device to the internet.
2. The employee opens the organization's VPN client.
3. The VPN authenticates the employee.
4. An encrypted connection, called a VPN tunnel, is established.
5. The employee can securely access authorized company resources.

### Benefits of VPN

1. **Encryption:** Protects data while it travels across the network.
2. **Remote Access:** Allows employees to access company resources from different locations.
3. **Authentication:** Verifies the identity of users before granting access.
4. **Privacy:** Helps protect network traffic from unauthorized observation.

### Risks of a Poorly Configured VPN

1. Weak passwords may allow unauthorized access.
2. Missing multi-factor authentication increases account takeover risks.
3. Outdated VPN software may contain security vulnerabilities.
4. Incorrect access permissions may expose sensitive company resources.
5. Poor network configuration may allow unauthorized traffic.

### Example

If a company allows VPN access using only weak passwords, an attacker who discovers a password may gain unauthorized access to the company's internal network.

### Conclusion

A VPN provides a secure way for remote employees to access company resources. Proper authentication, encryption, software updates, and access controls are important for maintaining VPN security.














## Q8. Network Troubleshooting

### Scenario

A computer can communicate with other devices on its local network but cannot access the internet.

This may indicate a problem with the default gateway, router, internet connection, DNS, or routing configuration.

### Ordered Troubleshooting Steps

**1. Check IP Configuration**

Command:
`ip addr`

Purpose: Checks network interfaces, their status, and assigned IP addresses.

**2. Check the Default Gateway**

Command:
`ip route`

Purpose: Checks whether a default route exists and identifies the gateway address.

**3. Test the Local Gateway**

Command:
`ping -c 4 192.168.1.1`

Purpose: Checks whether the computer can communicate with its router. Replace the example address with the actual gateway address.

**4. Test External IP Connectivity**

Command:
`ping -c 4 8.8.8.8`

Purpose: Checks connectivity to an external IP address without depending on DNS.

**5. Test DNS Resolution**

Command:
`nslookup google.com`

Purpose: Checks whether DNS can translate a domain name into an IP address.

**6. Trace the Network Route**

Command:
`traceroute 8.8.8.8`

Purpose: Displays the network hops between the computer and the destination to help identify possible routing problems.

### Interpreting Troubleshooting Results

| Test Result | Possible Problem |
|---|---|
| No valid IP address | DHCP or network interface problem |
| Gateway ping fails | Local network or router problem |
| Gateway works but external IP fails | Router, ISP, or upstream routing problem |
| External IP works but domain lookup fails | DNS problem |
| Traceroute stops at a particular hop | Possible routing or traffic filtering issue |

Note: A firewall may block ping or traceroute traffic, so a failed test does not always mean the network is unavailable.

### Conclusion

Network troubleshooting should be performed systematically, starting with local IP configuration and progressing towards the gateway, external connectivity, DNS, and routing. This approach helps identify network problems efficiently.