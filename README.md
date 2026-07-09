# persoanl-home-lab

## Hardware Specifications

### 1. BEAST (Core Gateway & Workstation & gaming pc)
*   **CPU:** AMD Ryzen 3 3300X (4 Cores, 8 Threads)
*   **GPU:** NVIDIA GeForce RTX 4060 Ti
*   **RAM:** 32 GB (2x16GB) DDR4 @ 3600 MHz
*   **Storage:** 
    *   500 GB M.2 NVMe SSD
    *   1 TB M.2 NVMe SSD
*   **Role in Lab:** Core Network Bus & Pop!_OS Gateway / AAA Captive Portal.

### 2. NEXUS_MID (AsusPro E830)
*   **CPU:** Intel Core i5-4770 vPro (4 Cores, 8 Threads)
*   **RAM:** 16 GB (2x8GB) SODIMM DDR3 @ 1600 MHz
*   **Storage:** 1 TB SATA SSD
*   **Role in Lab:** Primary Proxmox VE Virtualization Host.

### 3. NEXUS_COMPUTE (Asuspro Headless Laptop)
*   **CPU:** Intel Core i3 (10th Gen)
*   **RAM:** 12 GB SODIMM DDR4 @ 3200 MHz
*   **Storage:** 
    *   512 GB M.2 NVMe SSD
    *   1 TB SATA HDD (Planned addition for VM/Server storage storage)
*   **Role in Lab:** Secondary Proxmox VE Node / Dedicated Physical Compute Node.

### 4. ZOMBI_PC (Future NAS)
*   **CPU:** Intel Core CPU
*   **RAM:** 16 GB (4x4GB) DDR3 @ 1600 MHz
*   **Storage:** *TBD (To Be Determined - Storage drive selection in progress)*
*   **Role in Lab:** Dedicated Network Attached Storage (NAS) & Media Storage (NFS/SMB).

