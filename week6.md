## Introduction

This week focused on two important networking concepts: ARP (Address Resolution Protocol) and default gateways. The lab helped in understanding how devices identify each other in a LAN and how routing works across multiple subnets.

---

## Task 1: ARP (IP to Hardware Address Resolution)

### Aim
To observe how ARP maps IP addresses to MAC (hardware) addresses in a network.

---

### Setup

Project used:
Setting-IP-12309264  

Devices:
- 4 Linux Hosts  
- 1 Ethernet Switch  

---

### Steps Performed

1. Viewed ARP table on Host A:

Command:
ip neigh show  

2. Initially, the ARP table was mostly empty or had limited entries.

---

### Ping Test 1

From Host A:
ping 10.1.1.2  

After ping:
- ARP table updated  
- Entry added for Host B  
- MAC address mapped to IP  

---

### Ping Test 2

From Host C:
ping 10.1.1.1  

Then checked ARP table on Host A again.

---

### Observation

- New entries appeared after communication  
- Each entry showed:
  - IP address  
  - MAC address  
  - State (e.g., REACHABLE)  

This shows ARP works automatically when devices communicate.

---

### Outputs

- ARP-Basics-12309264-HostA-Table.png  
- Additional ARP screenshots (optional)  

---

## Task 2: Default Gateway

### Aim
To configure routing between multiple subnets using default gateways.

---

### Network Setup

Project:
Default-Gateway-12309264  

Topology included:
- 4 Linux Hosts  
- 2 Linux Routers  
- 2 Ethernet Switches  

Total Subnets: 3  

---

### IP Configuration Example

Subnet 1:
- Host1 → 10.1.1.1  
- Host2 → 10.1.1.2  
- Router1 → 10.1.1.254  

Subnet 2:
- Host3 → 10.2.2.1  
- Host4 → 10.2.2.2  
- Router2 → 10.2.2.254  

Router-to-Router:
- Router1 → 10.3.3.1  
- Router2 → 10.3.3.2  

---

### Configuration

Each device configured using:

/etc/network/interfaces  

Hosts:
- Set IP address  
- Set default gateway  
- Disabled forwarding  

Routers:
- Set IP addresses on interfaces  
- Enabled forwarding  

---

### Commands Used

Check routing table:
ip route show  

Check forwarding:
sysctl net.ipv4.ip_forward  

---

### Testing

Ping was performed between hosts in different subnets.

Result:
- Successful communication  
- Routing worked correctly via routers  

---

### Outputs

- Default-Gateway-12309264.gns3project  
- Default-Gateway-12309264-network.png  
- Routing table records  
- Default-Gateway-12309264-ping.png  

---

## Learning

- Learned how ARP maps IP to MAC  
- Understood how ARP table updates dynamically  
- Learned default gateway usage  
- Practiced routing across multiple subnets  

---

## Conclusion

Week 06 improved my understanding of how communication happens inside a LAN using ARP and how devices communicate across networks using default gateways. These concepts are essential for troubleshooting and network design.
