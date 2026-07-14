
# 🏃‍♂️ Active Sprint Tracker: Phase A (Core Network & Hypervisors)

> **Sprint Objective:** Get all physical hardware ready, clean install our Proxmox hypervisors, and configure secure local and remote access via ZeroTier and the TP-Link AP.

---

## 📋 Active Tasks for This Week

### 1. 🔌 Hardware Staging
- [ ] 🔵 **AsusPro E830:** Perform a complete drive wipe, verify/update the BIOS to the latest manufacturer version to ensure stable virtualization support.
- [ ] 🔵 **NEXUS_COMPUTE:** Physically open the laptop chassis and install the secondary 1TB SATA HDD for future VM expansion.
- [ ] 🔴 **ZOMBI_PC:** Assemble the hardware components on the workbench, identify all available spare storage drives, and perform initial POST diagnostics.

### 2. 🎛️ Hypervisor Installation
- [ ] 🔵 Clean install **Proxmox VE** on the **AsusPro E830** (Primary). Assign static local IP.
- [ ] 🔵 Clean install **Proxmox VE** on the **NEXUS_COMPUTE** (Secondary). Assign static local IP.

### 3. 🌐 Secure Remote SDN & Local AP Setup
- [ ] 🟠 Register and authorize **BEAST** (Pop!_OS) as our core ZeroTier Gateway.
- [ ] 🟢 Reconfigure the **Lenovo IdeaPad 1** as our secure Command Center client.
- [ ] 🔴 Reset the **TP-Link RE305** and configure it strictly in **Access Point (AP) Mode** wired to the local switch.
- [ ] 🟠 Verify local SSH access and end-to-end ZeroTier network ping tests across all devices.

### ✍️ 4. GitHub DevLog Setup
- [ ] 🟢 Initialize the first thread on **GitHub Discussions** to document our hardware setup and log initial hypervisor installation notes.
