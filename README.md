# Setshaba Conveyancers - Network Design Portfolio

**Module:** CMPG 325  
**Student:** Mokolo, MC (46547894)  
**Project ID:** CMPG325-2026-081  
**Client ID:** CLI-081  
**Organisation:** Setshaba Conveyancers (Potchefstroom)  
**Industry:** Legal Services  

## Project Overview
This repository contains the network design, simulation, and technical documentation for Setshaba Conveyancers, a small legal services firm located in Potchefstroom. The network is simulated using Cisco Packet Tracer and is designed to provide secure, scalable connectivity for management, conveyancing staff, administration, reception, and a central server.

## Key Requirements & Constraints
* **Assigned Addressing Block:** `10.34.0.0/16`
* **Design Constraint:** Guest users must not reach internal resources.
* **Client Change Request (CR14):** After-hours cleaning/security contractors require limited wireless access.
* **Assigned Networking Challenge:** SSH (Secure device management plane) - Replacing unencrypted Telnet with local authentication, RSA keys, and VTY line restrictions on Layer 3 devices.

## Network Design Strategy
The `10.34.0.0/16` address space is subnetted using VLSM into `/24` networks mapped directly to departmental VLANs. This hierarchical approach limits broadcast domains, organizes traffic, and allows for strict Layer 3 Access Control Lists (ACLs) to enforce security constraints on guest and contractor traffic.

### IP Addressing & VLAN Summary
| VLAN | Name | Subnet | Gateway | Notes |
|---|---|---|---|---|
| 10 | Management | `10.34.10.0/24` | `10.34.10.1` | Internal |
| 20 | Conveyancing | `10.34.20.0/24` | `10.34.20.1` | Internal |
| 30 | Admin/Finance | `10.34.30.0/24` | `10.34.30.1` | Internal |
| 40 | Reception | `10.34.40.0/24` | `10.34.40.1` | Internal |
| 50 | Servers | `10.34.50.0/24` | `10.34.50.1` | Internal |
| 60 | Guest Wi-Fi | `10.34.60.0/24` | `10.34.60.1` | Internet-only, ACL-isolated |
| 70 | Contractor (CR14) | `10.34.70.0/24` | `10.34.70.1` | Internet-only, time-restricted ACL |
| 99 | Native/Trunk | `10.34.99.0/24` | N/A | No hosts |

## Repository Structure
```text
setshaba-conveyancers-network/
|-- README.md
|-- docs/
|   |-- 01-client-requirements.md
|   |-- 02-physical-topology.png
|   |-- 03-logical-topology.png
|   |-- 04-ip-addressing-plan.md
|   |-- 05-cr14-design.md
|-- packet-tracer/
|   |-- setshaba-conveyancers-network.pkt
|-- config/
|   |-- router0-config.txt
|   |-- switch0-config.txt
|   |-- sw-conveyancing-config.txt
|   |-- sw-admin-reception-config.txt
|   |-- sw-servers-config.txt
|   |-- isp-config.txt
|   |-- cr14-after-hours.txt
|   |-- cr14-business-hours.txt
|-- evidence/
|   |-- screenshots/   (T1 to T13)
|   |-- testing/
|-- video/
|   |-- demo-link.md

```

## Milestones
* **Milestone 1:** Client Design (28 August 2026)
* **Milestone 2:** Implementation & Initial Testing (2 October 2026)
* **Final Submission:** Full working network & demonstration (16 October 2026)

---


