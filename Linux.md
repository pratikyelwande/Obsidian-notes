## Linux Booting Process 

---

### 🟩 **Step 1: Power On and POST (BIOS/UEFI)**

- You press the **power button**.
    
- The system runs **POST** (Power-On Self-Test) to check hardware like CPU, RAM, keyboard.
    
- BIOS/UEFI is in control at this stage.
    
- BIOS/UEFI now looks for a **bootable device** (hard drive, SSD, USB, etc.).
    

✅ **Who's in charge?** → BIOS/UEFI  
✅ **What's it doing?** → Checking hardware and finding bootable disk.

---

### 🟨 **Step 2: Find and Load the MBR**

- BIOS (not UEFI) looks at the **first sector (sector 0)** of the first bootable device.
    
- That first 512-byte sector is called the **MBR (Master Boot Record)**.
    

#### MBR Contains:

1. **Bootloader (Stage 1)** → Small code to start boot process.
    
2. **Partition table** → Describes where Linux is installed on the disk.
    

📌 **MBR is the "first code" loaded from the disk by BIOS.**

✅ **Who's in charge?** → BIOS loads and executes code from the MBR.  
✅ **Where is MBR?** → First 512 bytes of the bootable device (`/dev/sda`, for example).

---

### 🟧 **Step 3: Bootloader Takes Over (e.g. GRUB)**

- MBR’s bootloader code is small, so it typically loads the **next stage of GRUB** (usually found in the `/boot` partition).
    
- GRUB now displays the **boot menu** (e.g., Ubuntu, Advanced options, etc.).
    
- You (or GRUB automatically) choose which kernel or OS to boot.
    

✅ **Who's in charge?** → GRUB (full bootloader).  
✅ **What’s it doing?** → Loads Linux **kernel** and **initramfs** into memory.

---

### 🟥 **Step 4: Kernel Loads**

- The Linux **kernel** (like `/boot/vmlinuz-xxx`) gets loaded into memory.
    
- The kernel starts running.
    
- It also uses the **initramfs** — a temporary file system — to help mount your real root filesystem.
    

✅ **Who's in charge?** → Linux Kernel  
✅ **What’s it doing?** → Gets system ready and prepares real Linux environment.

---

### 🟦 **Step 5: Switch to Real Root File System**

- `initramfs` hands control to the real Linux system by running `/sbin/init`.
    
- The **real root partition** (e.g., `/dev/sda2`) is mounted.
    
- Kernel now runs the **init system** from your actual Linux install.
    

✅ **Who's in charge?** → Now running from your actual Linux system.

---

### 🟪 **Step 6: init System Starts (Usually systemd)**

- The first user-space program, **init** (usually `systemd`), starts.
    
- `systemd` launches system services like:
    
    - Network
        
    - Display manager
        
    - Logging
        
    - File systems
        

✅ **Who's in charge?** → `systemd` (or other init like SysVinit)

---

### ⬛ **Step 7: Login Screen Appears**

- You finally see:
    
    - A terminal login (for CLI), or
        
    - A GUI login screen (like GNOME, KDE).
        
- Once you log in, your Linux desktop or shell starts.
    

✅ **Who's in charge?** → Your Linux session is now fully running!

---

## 🔁 Summary Table: Boot Process with MBR

|Step|Who’s in Charge|Key Component|Description|
|---|---|---|---|
|1|BIOS/UEFI|POST|Checks hardware, finds bootable device|
|2|BIOS|MBR (sector 0 of disk)|Loads tiny bootloader code|
|3|GRUB|/boot/grub|Shows menu, loads kernel & initramfs|
|4|Linux Kernel|vmlinuz|Starts OS core, loads drivers|
|5|initramfs|temporary FS|Finds and mounts real root|
|6|systemd/init|`/sbin/init`|Starts system services|
|7|User|Login manager|You log in and use Linux!|

---
## 📁 **Linux Directory Structure** (starting from `/`)

---

### 📂 **Detailed Explanation of Each Directory**

|Directory|Description|
|---|---|
|`/`|Root directory – the top of the filesystem hierarchy. Everything starts here.|
|`/bin`|Essential **binary** programs (like `ls`, `cp`, `mv`) needed for basic system operation.|
|`/boot`|Contains bootloader files (like **GRUB**, **vmlinuz**, and **initramfs**).|
|`/dev`|Contains **device files** (e.g., `/dev/sda` for disks, `/dev/tty` for terminals).|
|`/etc`|System **configuration files** (e.g., network, users, services, etc.).|
|`/home`|Personal directories for all **regular users** (e.g., `/home/john`).|
|`/lib`|Essential **shared libraries** used by binaries in `/bin` and `/sbin`.|
|`/media`|Auto-mounted **removable media** (USBs, CDs) go here.|
|`/mnt`|Temporary mount point for mounting filesystems manually.|
|`/opt`|Optional/add-on **third-party software** (e.g., custom apps, Chrome).|
|`/proc`|Virtual filesystem with **process and kernel info** (`/proc/cpuinfo`, etc.).|
|`/root`|Home directory of the **root user** (admin account), not `/home/root`.|
|`/run`|Runtime data like PIDs, sockets – cleared at reboot.|
|`/sbin`|System **binaries** for system admin tasks (e.g., `fsck`, `reboot`).|
|`/srv`|Data for services (like HTTP, FTP) hosted on the system.|
|`/sys`|Virtual directory for **kernel and hardware info** – used by udev and drivers.|
|`/tmp`|Temporary files – deleted at reboot or manually.|
|`/usr`|User-level programs and data. Often the largest directory. Contains:|

- `/usr/bin`: Most user commands
    
- `/usr/lib`: Shared libraries
    
- `/usr/share`: Documentation, icons, etc.  
    | `/var` | Variable data: **logs**, **databases**, **spools**, **mail**, etc. |

ls -lha - use for human readable format.
file [filename] - shows which type of file it is.
type - used to find which type of file it is.
alias- set custom commands
