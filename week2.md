## Introduction
This week focused on configuring static IP addresses in different ways and testing network connectivity using ping.

---

## Task 1: Static IP Configuration

### Network Setup
Project: Setting-IP-12316847  

Devices used:
- 4 Linux Hosts  
- 1 Ethernet Switch  

Network: 10.1.1.0/24  

Assigned IPs:
- Host1 → 10.1.1.1  
- Host2 → 10.1.1.2  
- Host3 → 10.1.1.3  
- Host4 → 10.1.1.4  

---

### Method 1: GNS3 Configure
Used for Host1 and Host2.  
IP assigned before starting the node.

---

### Method 2: /etc/network/interfaces
Used for Host3.

Configuration:
auto eth0  
iface eth0 inet static  
    address 10.1.1.3  
    netmask 255.255.255.0  

Commands:
ifdown eth0  
ifup eth0  

---

### Method 3: ip command
Used for Host4.

Command:
ip address add 10.1.1.4/24 dev eth0  

---

### Verification
Command used:
ip address show  

All hosts showed correct IP addresses.

---

## Task 2: Ping Testing

### Basic Ping
ping 10.1.1.2  

Result: Successful communication, no packet loss.

---

### Invalid Ping
ping 10.1.1.100  

Result: No response, 100% packet loss.

---

### Ping with Options
ping -c 5 -i 2 -s 100 10.1.1.2  

---

## Outputs
- Setting-IP-12316847.gns3project  
- Network screenshot  
- Host IP screenshots  
- Ping screenshots  

---

## Learning
- Learned 3 ways to assign IP  
- Understood ping and RTT  
- Practiced network testing  

---

## Conclusion
This lab improved my understanding of IP configuration and network connectivity testing.
