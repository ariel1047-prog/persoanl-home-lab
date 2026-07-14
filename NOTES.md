
# 📝 NEXUS Internal Scratchpad & Self-Notes

This is a private-facing developer log used to dump temporary commands, active IP configurations, hardware check outputs, and error logs during the build process.

---

## 📌 Quick Reference Data

### 🔴 physical Network Connections (Switch Topology)
* **Port 1:** `BEAST` (Pop!_OS Gateway / Workstation)
* **Port 2:** `AsusPro E830` (Primary Proxmox Host)
* **Port 3:** `NEXUS_COMPUTE` (Secondary Headless Laptop Node)
* **Port 4:** `TP-Link RE305` (Configured in Wireless AP Mode)
* **Port 5:** *[Uplink to Main Router / Internet]*

### 🔵 Active IP Addressing Pool (Local Subnet)
* **AsusPro E830 (Proxmox GUI):** `https://[IP]:8006`
* **NEXUS_COMPUTE (Proxmox GUI):** `https://[IP]:8006`
* **TP-Link RE305 AP Gateway:** `http://[IP]`

### 🟠 SDN & Remote Access (ZeroTier Topology)
* **ZeroTier Network ID:** `[Insert Network ID Here]`
* **Authorized Gateways:** * `BEAST` (Pop!_OS) — Metric: Gateway
  * `Lenovo IdeaPad 1` (Client) — Metric: Admin Client
  * `Samsung Galaxy S23 Ultra` (Client) — Metric: Mobile Client

---

## 🛠️ CLI Cheat-sheets & Active Troubleshooting

*Use this section to dump useful terminal commands used during the setup of Proxmox, ZeroTier, or pfSense.*

### 🔵 Proxmox Post-Install Tweaks (PVE No-Subscription Repository)
```bash
# Example placeholder for removing subscription nag and enabling no-subscription repo:
# apt-get update && apt-get install -y ...

---

### 🟠 ZeroTier CLI Essentials

# Join network
sudo zerotier-one -q join <network-id>

# Check status
sudo zerotier-one -q status












