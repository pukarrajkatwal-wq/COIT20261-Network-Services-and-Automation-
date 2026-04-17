## Introduction

This week covered two important networking topics: viewing routing tables in a small routed network and observing how dynamic routing with OSPF responds to link failure. These activities helped me understand how routers make forwarding decisions and how routing protocols can automatically adjust when the network changes.

---

## Task 1: View Routing Tables

### Aim
The aim of this task was to learn how to configure a simple routed network, view routing tables, and test communication between two different subnets.

---

### Network Topology

For this task, I created a project named:

`View-Routes-12309264`

The topology included:
- 3 Linux Hosts  
- 1 Linux Router  
- 1 Ethernet Switch  

The network was divided into two subnets:
- Subnet 1 connected Host1, Host2, and one router interface through the switch  
- Subnet 2 connected Host3 directly to the router  

---

### IP Addressing

A separate IP network was used for each subnet. One suitable example setup is shown below:

#### Subnet 1
- Host1 → 10.1.1.1/24  
- Host2 → 10.1.1.2/24  
- Router eth0 → 10.1.1.254/24  

#### Subnet 2
- Host3 → 10.2.2.1/24  
- Router eth1 → 10.2.2.254/24  

For the hosts, the router interface in the same subnet was set as the default gateway.

---

### Forwarding Configuration

Forwarding was enabled on the router and disabled on all hosts.

- Router: `up sysctl net.ipv4.ip_forward=1`
- Hosts: `up sysctl net.ipv4.ip_forward=0`

This allowed the router to pass packets between the two subnets while keeping the hosts as end devices only.

---

### Commands Used

To check the forwarding status:
```bash
sysctl net.ipv4.ip_forward
```

To display the routing table:
```bash
ip route show
```

---

### Routing Table Observation

Each device showed different routing information depending on its role.

- **Hosts** displayed a directly connected route for their local subnet and a default route pointing to the router.
- **Router** displayed both directly connected subnets, allowing it to forward traffic between them.

This showed clearly that the router had knowledge of both networks, while hosts relied on the gateway for any destination outside their own subnet.

---

### Ping Test

A successful ping was performed from a host in one subnet to a host in the other subnet. This confirmed that:
- IP addresses were configured correctly  
- Default gateways were set properly  
- Router forwarding was working  

---

### Outputs for Task 1

The required outputs for this task were:
- `View-Routes-12309264.gns3project`
- `View-Routes-12309264-network.png`
- Record of IP addresses and routing tables
- `View-Routes-12309264-ping.png`

---

## Task 2: Dynamic Routing with OSPF

### Aim
The purpose of this task was to observe how OSPF works in a multi-router environment and how routing changes automatically when a link becomes unavailable.

---

### Project Setup

For this activity, the provided OSPF template project was imported and duplicated using the required naming style.

The network already included:
- 2 Hosts  
- 4 FRR Routers  
- 2 NETem nodes  

The IP addresses and OSPF configuration were already completed in the template, so no manual routing configuration was required.

---

### Starting the Routers

After starting the project, I waited until all FRR routers finished booting and displayed the `frr#` prompt. If the router showed `frr:~#`, the `vtysh` command was used to enter FRR mode.

---

### FRR Commands Used

The following commands were used to inspect routing information:

```bash
show ip ospf neighbor
show ip ospf route
show ip route
```

These commands helped identify:
- Neighbour router IP addresses  
- OSPF-learned destination networks  
- Next-hop routers used to reach those networks  
- Routes installed in the Linux routing table  

---

### Path Testing

To test the route between the two hosts, `traceroute` was used:

```bash
traceroute <destination-ip>
```

This showed the sequence of routers used along the path from one host to the other.

---

### Link Failure Test

After observing the original path, one NETem node on the active path was stopped. This effectively disconnected that link.

`traceroute` was then run again until a different path was shown. This demonstrated that OSPF automatically detected the link failure and recalculated a new route through the remaining available routers.

---

### Summary of Observation

From this task, I observed that:
- OSPF dynamically learns routes between routers  
- Routers exchange information with neighbours automatically  
- If one path fails, another valid path can be selected without manually changing routes  
- Dynamic routing is more flexible than static routing in larger networks  

---

### Outputs for Task 2

The required outputs for this task were:
- `OSPF-Basics-12309264.gns3project`
- `OSPF-Basics-12309264-network.png`
- Output showing neighbour routers of FRR1
- Output showing routing table for two routers
- Summary table of destination and next node for all routers
- `traceroute` output before and after disconnecting the link

---

## Learning Reflection

This week gave me a much better understanding of how routers operate in real networks. In Task 1, I learned the difference between a host routing table and a router routing table, and I saw why forwarding must be enabled on a router. In Task 2, I learned that OSPF can automatically adapt to network failures and find an alternative path when one route is no longer available.

The practical work made routing concepts much easier to understand than only reading theory.

---

## Conclusion

Week 04 was very useful in building my understanding of routing. The first task helped me learn the basics of routing tables and forwarding between subnets, while the second task introduced me to dynamic routing with OSPF. Together, these activities showed how networks move traffic efficiently and continue operating even when conditions change.
