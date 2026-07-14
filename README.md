
# Personal Home Lab — AKA NEXUS

---

## 🌐 Lab Architecture & Role Distribution

### Core Integrations
* 🟠 **ZeroTier:** Secure Site-to-Point Mesh VPN Gateway.
* 🔴 **pfSense:** Core Firewall & Network Routing.
* 🟠 **Vaultwarden (PassSafe):** Self-hosted password management (secured via DuckDNS).
* 🔴 **Jellyfin / SMB / NFS:** Media streaming and central network storage management.

### 1. BACKEND (Core Services & Storage) — 🔴
* 🔴🟠 **BEAST (Host OS: Pop!_OS - X11 Base):** * Functions as the Core Network Bus, Pop!_OS Gateway, and AAA Captive Portal.
    * *Network Expansion:* A separate partition from a 1 TB hard drive (connected to the E830) will be routed here to host a dedicated **pfSense VM** for advanced network routing.
* 🔴 **ZOMBI_PC:** * Dedicated Network Attached Storage (NAS) hosting central Media Storage via NFS/SMB shares.

### 2. MID (Compute & Virtualization Layers) — 🔵
* 🔵 **AsusPro E830:** 🔵 *Primary Proxmox VE Virtualization Host.*
* 🔵 **Asuspro Headless Laptop:** 🔵 *Secondary Proxmox VE Node (Configured for compute extension and future High Availability clustering).*

### 3. FRONTEND (User Access & Client Interface) — 🟢
* 🟢 **BEAST (Host OS Interface):** Used as a Daily Workstation & Gaming PC.
* 🟢 **Asuspro Headless Laptop (Virtual Machines):**
    * 🟢 **Mail Server** — *Active Communication Host*
    * 🟢🔴 **Media Server (Jellyfin)** — *Active Streaming Instance (Storage mapped to Backend)*
    * 🟢🟠 **PassSafe (Vaultwarden)** — *Active Credential Store (Secured via DuckDNS)*
* 🟢 **ZOMBI_PC (Isolated VM Environment):**
    * 🟢 **Windows 7 Legacy OS Sandbox** — *Planned Environment with Direct GPU Passthrough optimized for retro gaming and hardware benchmarking.*
* 🟢 **Lenovo IdeaPad 1:** Used as the primary system administration client and command center.
* 🟢 **Samsung Galaxy S23 Ultra:** Mobile client for remote infrastructure monitoring and credential access.

---

## 🔐 Identity, Access Management (IAM) & User Experience — 🟠

### Centralized User Access Control (RBAC Architecture)
To enforce security best practices, the environment utilizes a Role-Based Access Control (RBAC) model with three distinct user profiles:
1. 🔵 **Domain/Infrastructure Admin:** High-privilege account dedicated solely to system administration, virtualization management (Proxmox Cluster), and core networking modifications.
2. 🟠 **Security & Passwords User:** A restricted, dedicated account used exclusively for accessing **Vaultwarden (PassSafe)** credential stores.
3. 🟢 **Media & Entertainment User:** A low-privilege consumer account provisioned specifically for streaming services via **Jellyfin** and accessing local **NFS/SMB** shares on the ZOMBI_NAS.

### 🌐 High-Availability Internal Web Portal & Vault Storage
To ensure seamless access and eliminate single points of failure (SPOF):
* **Distributed Web Dashboards:** Two identical Internal Web Portals (Dashboards) are deployed. The primary dashboard runs as a VM on the **Asuspro Headless Laptop** (🟢 Active), while a secondary replica runs on the **ZOMBI_PC** as a hot-standby backup (🟢/🔴 Planned).
* **Decoupled Password Vault Architecture:** * *Compute Layer (Mid - 🔵):* The Vaultwarden application instance runs as a dedicated VM on the **Asuspro Headless Laptop** for optimized processing and isolation.
    * *Storage & Persistence Layer (Backend - 🔴):* The encrypted database and runtime data are directly mapped and backed up onto the **ZOMBI_NAS** via secure network shares (NFS/SMB), decoupling the application from the underlying storage.

### 🌐 Secure Remote Access & SDN (Software-Defined Networking) — 🟠
To facilitate seamless and secure management from external networks (e.g., accessing the lab via the Lenovo IdeaPad 1 from a remote location), the infrastructure leverages **ZeroTier** as an SDN overlay.
* **Zero-Trust Remote Access:** Eliminates port-forwarding or traditional corporate VPNs. All external client devices run the ZeroTier client daemon.
* **Encrypted Peer-to-Peer Tunnels:** Establishes an encrypted end-to-end tunnel directly to the **BEAST (ZeroTier Mesh Gateway)**. 
* **Seamless Local Experience:** Remote clients are logically bridged into the core network topology, allowing transparent access to the internal Web Portals, Proxmox Cluster management interfaces, and Vaultwarden storage using internal private IP addressing.

---

## 🖥️ Hardware Bill of Materials (BOM)

| Device Name | Layer | CPU | GPU | RAM | Storage | Primary Role |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **BEAST** | 🔴🟠🟢 | AMD Ryzen 3 3300X <br>*(4C / 8T)* | NVIDIA RTX 4060 Ti <br>*(8GB)* | 32 GB DDR4 <br>@ 3600 MHz | 512GB M.2 NVMe SSD <br>1TB M.2 NVMe SSD | Core Network Bus, Pop!_OS Gateway, AAA Captive Portal, Workstation & Gaming PC |
| **AsusPro E830** | 🔵 | Intel Core i5-4770 vPro <br>*(4C / 8T)* | Integrated Intel HD | 16 GB DDR3 SODIMM <br>@ 1600 MHz | 1 TB SATA SSD | NEXUS_MID: Primary Proxmox VE Virtualization Host |
| **NEXUS_COMPUTE** | 🔵 | Intel Core i3 <br>*(10th Gen)* | Integrated Intel HD | 12 GB DDR4 SODIMM <br>@ 3200 MHz | 512GB M.2 NVMe SSD <br>1TB SATA HDD *(Planned)* | Secondary Proxmox VE Node *(Dedicated Compute Node)* |
| **ZOMBI_PC** | 🔴🟢 | Intel Core CPU <br>*(Legacy)* | *GPU Selection TBD* <br>*(R9 390 / GTX 560 / RX 550)* | 16 GB DDR3 <br>*(4x4GB @ 1600 MHz)* | *TBD (Storage drive selection in progress)* | Future NAS & Legacy OS Sandbox Environment |

### Network Infrastructure & Clients — 🟢
* **Switch:** TP-Link LS105G (5-Port Desktop Gigabit Switch)
* **Access Point:** TP-Link RE305 (AC1200 Wi-Fi Extender configured in AP Mode)
* **Client Laptop (Lenovo IdeaPad 1):** 🟢 AMD Ryzen 7 5700U, Radeon Graphics, 16GB DDR4 @ 3200 MHz
* **Client Mobile (Samsung Galaxy S23 Ultra):** 🟢 Dynamic AMOLED 2X, Snapdragon 8 Gen 2, 12GB RAM
