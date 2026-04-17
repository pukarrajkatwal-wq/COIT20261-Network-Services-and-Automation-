## 1. Introduction

This week focused on using Netcat for simple communication between devices and capturing network packets in GNS3. The lab helped in understanding application-level communication and basic packet analysis.

---

## 2. Task 1 – Netcat Communication

### Aim
To learn how to use Netcat (nc) for communication between two hosts.

---

### Setup

Project used:
Setting-IP-12309264  

Devices:
- 4 Linux Hosts  
- 1 Ethernet Switch  

---

### Steps Performed

#### Server (Host A)
Command:
nc -l -p 5000  

#### Client (Host B)
Command:
nc 10.1.1.1 5000  

---

### Communication Test

Messages sent:

From Client → Server:
Pukar Katwal 

From Server → Client:
12309264

Both hosts successfully received messages.

---

### Output

Screenshot:
Netcat-Basics-12309264-client-server.png  

---

## 3. Task 2 – Packet Capture

### Aim
To capture packets and save them for analysis.

---

### Steps Performed

1. Started packet capture on link between Host A and Switch  
2. Ran ping command:

ping -c 3 10.1.1.2  

3. Used Netcat to send message between hosts  
4. Stopped capture  

---

### File Generated

Capture file:
Capture-Basics-12309264-ping-netcat.pcap  

---

## 4. Learning

- Learned how Netcat works as client-server tool  
- Understood difference between Ping and Netcat  
- Learned how to capture packets in GNS3  
- Gained idea about network traffic  

---

## 5. Conclusion

Week 03 helped in understanding real communication between devices and how data travels in a network. Packet capturing is useful for troubleshooting and analysis.
