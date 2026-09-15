# Multi-Server Network & Server Deployment Project

A hands-on system administration and networking project simulating a small multi-tier enterprise network deployed locally on VMware Workstation.

## 👥 Project Team
* Mornh Phkay [cite: 1]
* Neang Navin [cite: 1]
* Phon Piseth [cite: 1]
* Leav Vanny [cite: 1]
* **Instructor:** Buntha Chay [cite: 1]

---

## 🏗️ Architecture & Network Design
The network connects three Ubuntu-based virtual servers and a Windows client workstation through a shared Wireless HotSpot, which also routes traffic to the Internet.

### IP Addressing & Services Scheme
| Node Name | Role / Service | Static IP Address | Configured Domain |
| :--- | :--- | :--- | :--- |
| **VM1** | Web Server (HTTP / Apache2) | `10.11.125.10` | `mygroup.lab` |
| **VM2** | DNS Server (BIND9) | `10.11.125.20` | `ns.mygroup.lab` |
| **VM3** | File Server / Storage (SAMBA) | `10.11.125.30` | `files.mygroup.lab` |
| **Client PC** | Windows Workstation (Test Client) | Dynamic / Static (DNS: `10.11.125.20`) | — |

---

## ⚙️ Core Components & Configuration
* **Web Server (VM1):** Deployed on Ubuntu Server running HTTP/Apache2. Hosts the group's website accessible via both direct IP (`10.11.125.10`) and domain name (`mygroup.lab`).
* **DNS Server (VM2):** Configured using **BIND9** with a custom zone file and `A` records resolving `mygroup.lab` to the Web Server.
* **File Server (VM3):** Configured with **SAMBA** to enable secure file upload and download capabilities for the Windows client.
* **Remote Administration:** SSH service enabled on port 22 across all three Linux servers, managed remotely from the Windows client using **PuTTY**.

---

## 🧪 Testing & Verification
The following operational tests were successfully executed from the Windows Client workstation:
* [x] Bi-directional ping/reachability across all static IPs in the same subnet.
* [x] Remote SSH login to all three servers via PuTTY.
* [x] HTTP website loading via raw IP address (`10.11.125.10`).
* [x] HTTP website loading via DNS-resolved domain name (`mygroup.lab`).
* [x] File upload and download verification with the SAMBA File Server.

---

## 🛠️ Key Troubleshooting & Takeaways
* **IP Conflict Resolution:** Diagnosed and resolved a duplicate static IP address conflict between virtual machines, emphasizing the need for strict pre-deployment IP audit logs [cite: 1].
* **Virtualization Networking:** Gained practical understanding of VMware adapter behaviors across NAT, Host-only, and Bridged networking modes [cite: 1].
* **End-to-End DNS Flow:** Learned how to trace a DNS request from a Windows client resolver querying BIND9 (`10.11.125.20`) down to web service delivery.
