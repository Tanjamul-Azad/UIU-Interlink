# 🌐 UIU InterLink  
### Department-Based Network Infrastructure  
**Computer Networks Laboratory Project (CSE 3712)**

---

## 📌 Project Overview

**UIU InterLink** is a simulated **enterprise-level departmental network infrastructure** designed using **Cisco Packet Tracer**.  
The project models a university-like environment where multiple departments communicate securely and efficiently using **dynamic routing**, **automated IP allocation**, and **NAT-enabled public access**.

This project demonstrates practical implementation of:
- Network design & subnetting
- Dynamic routing using **OSPF**
- **DHCP** for automatic IP management
- **NAT** for simulated internet connectivity
- Enterprise-style hierarchical topology

---

## 🏫 Departments & Subnets

| Department | Subnet |
|----------|--------|
| HR | `192.168.10.0/26` |
| IT | `192.168.20.0/26` |
| Admin | `192.168.30.0/27` |
| Research | `172.16.10.0/26` |
| Public / Server | `198.51.100.0/24`, `203.0.113.0/24` |

🔗 **Point-to-Point Router Links:**  
`10.10.x.x /30`

---

## 🧱 Network Architecture

- Dedicated **routers and switches** per department  
- **Core backbone router** connecting all departments  
- **Public router** configured with NAT  
- Layered design for scalability and clarity  

📌 Built entirely in **Cisco Packet Tracer 8.x**

---

## ⚙️ Technologies & Protocols Used

- **Cisco Packet Tracer**
- **DHCP (Dynamic Host Configuration Protocol)**
- **OSPF (Open Shortest Path First)**
- **NAT (Network Address Translation)**
- **Static & Dynamic IP Subnetting**
- **Spanning Tree Protocol (PVST)**

---

## 🧪 Configuration Highlights
### 🔹 DHCP (Example)
```bash
ip dhcp excluded-address 192.168.10.1 192.168.10.10
ip dhcp pool HR
 network 192.168.10.0 255.255.255.192
 default-router 192.168.10.1
 dns-server 8.8.8.8

```
🔹 OSPF Routing
```
router ospf 1
 router-id 1.1.1.1
 network 192.168.10.0 0.0.0.63 area 0
 network 10.10.0.0 0.0.0.255 area 0
 passive-interface default
 no passive-interface fa0/1
```
🔹 NAT (Public Router)
```
access-list 10 permit 192.168.10.0 0.0.0.63
access-list 10 permit 192.168.20.0 0.0.0.63
access-list 10 permit 192.168.30.0 0.0.0.31
access-list 10 permit 172.16.10.0 0.0.0.63

interface fa5/0
 ip nat outside
interface fa0/0
 ip nat inside
ip nat inside source list 10 interface fa5/0 overload
```

🔍 Verification & Testing

Used industry-standard CLI commands:
```
show ip interface brief
show ip route
show ip dhcp binding
ping <destination-ip>
traceroute <destination-ip>
```

##🧑‍💻 Personal Contribution

Integrated all departmental networks

Troubleshot DHCP conflicts and gateway mismatches

Fixed OSPF adjacency and routing loop issues

Verified full end-to-end connectivity

Ensured stable, scalable, and optimized topology

##⚠️ Challenges Faced

Duplicate DHCP pools causing IP conflicts

Incorrect subnet masks and default gateways

OSPF routing failures due to missing network statements

Administratively down interfaces

Final-stage connectivity gaps

➡️ All issues were resolved through systematic testing and correction.

## ✅ Final Outcome

✔ Fully functional enterprise-style network
✔ Dynamic routing and automated IP allocation
✔ Scalable and realistic university network model
✔ Strong demonstration of real-world networking concepts

## 📂 Project Files

📄 Project Report (PDF)

🧩 Cisco Packet Tracer File (.pkt)

## 🎓 Academic Information

Course: Computer Networks Laboratory (CSE 3712)
Institution: United International University (UIU)
Author: Md.Tanzamul Azad


## 🏁 Conclusion

UIU InterLink successfully bridges theoretical networking concepts with hands-on implementation.
The project showcases a practical understanding of enterprise network design, routing protocols, IP management, and troubleshooting.



