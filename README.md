# Configuring Access Control List (ACL)

## Objective

This Access Control List (ACL) project focused on configuring standard ACLs to manage network traffic within a simulated environment using Cisco Packet Tracer. The primary goal was to establish rules that control access between devices, enhancing understanding of network security, traffic management, and the implications of access control in real-world scenarios.

### Skills Learned

- In-depth knowledge of Access Control Lists and their configuration on routers.
- Practical experience in configuring network devices to enhance security.
- Ability to analyze and understand the traffic flow within a network.
- Development of problem-solving skills related to network design and security policy implementation.
- Enhanced understanding of the implications of standard vs. extended ACLs.

### Tools Used

- Cisco Packet Tracer for simulating network configurations and ACL implementation.
- Command-Line Interface (CLI) for router configuration and testing connectivity.
- Network devices including laptops, PCs, servers, and routers for practical exercises.

## Steps

### Environment Setup

1. Packet Tracer Configuration: Download and open the provided Packet Tracer file. The environment includes pre-configured switches, routers, and computers to facilitate communication.

### Device Information:

- Laptop1: IP 10.10.10.10 / Subnet 255.255.255.0
- PC1: IP 10.10.10.100 / Subnet 255.255.255.0
- Server1: IP 192.168.1.150 / Subnet 255.255.255.0
- Router1: IP 10.10.10.1 / Subnet 255.255.255.0
- Router2: IP 192.168.1.1 / Subnet 255.255.255.0

--- 

Configuration of Standard ACLs

2. Access Control Configuration:

- Enter privileged mode on Router2:router> enable


- Create a standard ACL to deny Laptop1 access to Server1:router# configure terminal
router(config)# ip access-list standard 1
router(config-std-nacl)# deny host 10.10.10.10
router(config-std-nacl)# permit any

---

3. Apply ACL to Interface:

- Apply the created ACL to the interface Gi0/2 in an inbound direction:router(config)# interface gi0/2
router(config-if)# ip access-group 1 in

---

Testing Connectivity

4. Ping Tests:- Test connectivity from Laptop1 to Server1 (should fail):Laptop1> ping 192.168.1.150


- Test connectivity from PC1 to Server1 (should succeed):PC1> ping 192.168.1.150

---

Removing ACLs

5. Remove ACL and Reconfigure:

- Remove the existing ACL from Router2:router(config)# no ip access-list standard 1
router(config-if)# no ip access-group 1 in


- Create a new ACL that denies PC1 access to Server1 and apply it similarly:router(config)# ip access-list standard 2
router(config-std-nacl)# deny host 10.10.10.100
router(config-std-nacl)# permit any
router(config-if)# ip access-group 2 in

---

6. Final Connectivity Tests:

- Test connectivity from Laptop1 to Server1 (should succeed):Laptop1> ping 192.168.1.150


- Test connectivity from PC1 to Server1 (should fail):PC1> ping 192.168.1.150

Screenshots

Ref 1: ACL Configuration Example
ACL Configuration

Ref 2: Ping Test Results
Ping Test

---

### Conclusion

This project not only improved my technical skills in configuring ACLs but also provided insight into how these configurations can impact overall network security, preparing me for more complex security challenges in the future.
