
# 🗺️ NEXUS Project Roadmap & Progress Tracker

This roadmap outlines the systematic, multi-phase deployment of the NEXUS infrastructure. Tasks are broken down into logical execution phases and color-coded to align with the core architectural layers.

---

## 🏗️ Phase A: Core Network & Hypervisors (🔵/🔴/🟠 Focus)
*Goal: Establish physical hardware readiness, install base hypervisors, and configure baseline secure remote access.*

- [ ] **Hardware Staging:**
  - [ ] 🔵 Perform a clean format and run BIOS updates on the **AsusPro E830** (Primary Mid Node).
  - [ ] 🔵 Install the secondary 1TB SATA HDD into the **NEXUS_COMPUTE** laptop (Secondary Mid Node).
  - [ ]  🔴🟠 Configure dual-NIC IP Forwarding and NAT (iptables) on **BEAST** to route traffic and share internet from NIC1 (WAN) to NIC2 (NEXUS Switch).
  - [ ] 🔴 Physically assemble the **ZOMBI_PC** and map out available storage drives (Future Backend).
- [ ] **Hypervisor Installation:**
  - [ ] 🔵 Install clean **Proxmox VE** instances on both the **AsusPro E830** and **NEXUS_COMPUTE** with static IP configurations.
- [ ] **Secure Remote SDN & AP Setup:**
  - [ ] 🟠 Register the **BEAST** workstation as the primary ZeroTier Mesh Gateway.
  - [ ] 🟢 Configure the **Lenovo IdeaPad 1** as the administrative client/command center.
  - [ ] 🔴 Reset and configure the **TP-Link RE305** to AP Mode to establish the isolated local wireless network.
  - [ ] 🟠 Verify SSH access to all hosts via local network and secure ZeroTier tunnels.
- [ ] **GitHub & Community Setup:**
  - [ ] 🟢 Initialize the **GitHub Discussions** DevLog to document setup progress and command references.

---

## 🔐 Phase B: Virtualization Clustering & Routing (🔵/🔴 Focus)
*Goal: Cluster the hypervisors, implement split-brain prevention, and deploy core routing.*

- [ ] **Proxmox Clustering:**
  - [ ] 🔵 Join **AsusPro E830** and **NEXUS_COMPUTE** into a unified Proxmox VE Cluster.
- [ ] **Quorum & Split-Brain Prevention:**
  - [ ] 🔵🟠 Configure the **BEAST** workstation as an external **Corosync QDevice** to serve as the third voting member.
- [ ] **Core Firewall (pfSense):**
  - [ ] 🔴 Map the dedicated physical network partition to host the **pfSense VM** for advanced gateway routing and Captive Portal services.

---

## 💾 Phase C: Backend Central Storage (NAS) (🔴 Focus)
*Goal: Bring the dedicated NAS online and mount network shares to the virtualization cluster.*

- [ ] **ZOMBI_PC Diagnostics & OS:**
  - [ ] 🔴 Install a temporary testing OS on **ZOMBI_PC** to perform hardware stress testing and drive health checks.
  - [ ] 🔴 Wipe diagnostic drives and install the final NAS storage operating system.
- [ ] **Storage Shares:**
  - [ ] 🔴 Configure centralized NFS/SMB shares on the NAS.
  - [ ] 🔵🔴 Securely mount the NAS storage pools directly onto the Proxmox VE Cluster for VM backup and persistence.

---

## 🌐 Phase D: Frontend Services & Applications (🟢 Focus with 🔴/🟠 Integrations)
*Goal: Deploy internal VMs and applications, utilizing decoupled storage architecture.*

- [ ] 🟢 **Mail Server:** Deploy dedicated communications VM on the compute node.
- [ ] 🟢🔴 **Jellyfin Media Server:** Deploy streaming instance with media directories mounted directly to the NAS.
- [ ] 🟢🟠 **PassSafe (Vaultwarden):**
  - [ ] Deploy Vaultwarden VM on the compute node.
  - [ ] Configure DuckDNS for secure external SSL access.
  - [ ] Map Vaultwarden's database directories to save directly to the NAS (Decoupled Architecture).

---

## 👥 Phase E: IAM, UX & High Availability (🟠/🔵 Focus)
*Goal: Finalize Role-Based Access Control, deploy dual dashboards, and execute cluster failover testing.*

- [ ] **Identity & Access Management:**
  - [ ] 🟠 Implement strict RBAC with the 3 defined profiles (Admin, Security, Media).
- [ ] **HA Portals:**
  - [ ] 🟢 Deploy the primary Internal Web Portal (Dashboard) on the compute node and the secondary replica on the NAS.
- [ ] **Failover Testing:**
  - [ ] 🔵 Perform a hard shutdown on a Proxmox node to verify automatic VM high-availability migration and uninterrupted service access.

---

## 🎮 Phase F: Isolated Legacy Sandbox (🟢/🔵 Focus)
*Goal: Set up the isolated Windows 7 benchmarking and retro environment.*

- [ ] **VM Deployment:**
  - [ ] 🟢 Spin up a Windows 7 Legacy VM isolated from the production network.
- [ ] **GPU Passthrough:**
  - [ ] 🔵 Pass through the dedicated GPU on the host directly to the VM for bare-metal gaming/benchmarking performance (e.g., executing Crysis).
