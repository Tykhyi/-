# Laboratory Work No. 1
**Performed by student of group RPZ-33 Andrii Tykhyi**
## **Topic:** 
Introduction to the virtual machine working environment and features of the Linux operating system
## **Objective:**
1. Familiarization with different types of hypervisors and virtualization when working with operating systems.
2. Introduction to the main types of modern OSs and a brief overview of their capabilities.
## 1. Preparation tasks
### 1.1. Glossary of basic English terms
- **Virtual Machine (VM)** - Software emulation of a physical computer that executes programs like a real machine.<br>
- **Hypervisor** - Software that creates and runs virtual machines.<br>
- **Host OS** - The operating system of the physical computer on which the hypervisor (Type 2) runs.<br>
- **Guest OS** - The operating system installed inside the virtual machine.<br>
- **Kernel** - The core of the operating system, the central controller of everything that happens on the computer.<br>
- **Distribution (Distro)** - A set that includes the Linux kernel, GNU system utilities, and application software.<br>
- **CLI (Command Line Interface)** - A text interface where the user types commands from the keyboard.<br>
- **Open Source** - Software with open source code that can be freely viewed and modified. <br>
### 1.2. Characteristics of hypervisors. Their types. Main components and capabilities of XEN hypervisors.
- **Hypervisor** — is software that allows running multiple OSs on one physical computer simultaneously<br>

#### **Type 1 ("Bare-Metal"):**
- Installed directly on the server hardware without a main operating system.
- **Advantages:** High performance, stability.
- **Examples:** Xen, VMware ESXi, Microsoft Hyper-V (in server mode).
#### **Type 2 ("Hosted"):**
- Installed as a regular program on an existing operating system (Windows, Linux, macOS).
- **Advantages:** Easy to configure, suitable for home use.
- **Examples:** Oracle VirtualBox, VMware Workstation.
<br> **Xen** — is a Type 1 hypervisor (Bare-Metal), which is an Open Source project and is currently developed under the Linux Foundation.
#### **Main components and features:**
- **Paravirtualization:** This is the main "feature" of Xen. It allows the guest OS to interact with the hypervisor through special APIs, which significantly increases performance, bringing it closer to real hardware speed.
- **Architecture:**
<br><br>1. **Dom0 (Domain 0):** This is a special privileged virtual machine that starts first. It has direct access to hardware and manages other virtual machines.
<br><br>2. **DomU (User Domains):** These are regular guest virtual machines where your applications run.<br><br>
- **Security and isolation:** Thanks to its architecture, Xen ensures very reliable resource isolation, which is why it is often used in cloud services (for example, early versions of Amazon AWS were based on Xen).
- **Live Migration:** Allows moving a running virtual machine from one physical server to another without shutting it down or interrupting services.

## 2. Course of work

### 2.1. Stages of OS deployment based on VirtualBox
1.  **Preparation:** Downloading the operating system installation image (`.iso` file) and installing Oracle VM VirtualBox software.
2.  **Creating a Virtual Machine (VM):**
    * Clicking the "New" button.
    * Specifying the VM name, type (e.g., Linux), and version (e.g., Ubuntu 64-bit).
    * Allocating Random Access Memory (RAM).
    * Creating a virtual hard disk (VDI, fixed or dynamic size).
3.  **Media configuration:** In the VM settings ("Storage" section), we mount the downloaded ISO image into the virtual CD/DVD drive.
4.  **Launch and installation:** Starting the virtual machine, after which the standard Guest OS installation process begins (language selection, disk partitioning, user creation).
5.  **Installing additions:** After installing the OS, it is recommended to install "Guest Additions" for better screen integration and shared folders.

### 2.2. Hardware limitations when installing 32- and 64-bit OSs
* **Processor Architecture:** You can only install a 32-bit guest OS on a 32-bit processor (x86). On a 64-bit processor (x64), you can install both 32-bit and 64-bit systems.
* **Virtualization (VT-x/AMD-V):** To run 64-bit guest systems in VirtualBox, it is mandatory to support and **enable** hardware virtualization technologies (Intel VT-x or AMD-V) in the BIOS/UEFI of the physical computer (host).
* **RAM:** 64-bit systems consume more memory, so the host machine must have a sufficient RAM reserve.

### 2.3. Main stages of installing OS Linux in text mode
1.  **Loading the installer:** Selecting "Install" or "Install Ubuntu Server" in the bootloader menu.
2.  **Localization:** Selecting the interface language, country, and keyboard layout.
3.  **Network configuration:** Assigning a hostname and configuring the network interface (DHCP or static).
4.  **User configuration:** Entering the full name, login, and password for the main user (or root).
5.  **Disk Partitioning:** Creating partitions (automatically use the whole disk or manually: `/`, `/boot`, `/home`, `swap`).
6.  **Installing the base system:** Copying kernel files and main utilities.
7.  **Software selection:** (For example, OpenSSH server, Basic Ubuntu server), without selecting a graphical environment.
8.  **Installing the bootloader:** Installing GRUB into the Master Boot Record (MBR) or EFI partition.
9.  **Completion:** Rebooting the system and logging into the console.

### 2.4. Installing graphical shells (Gnome and KDE) in text mode
If Linux is installed without graphics (for example, Ubuntu Server), you can install the environment via the terminal using the package manager (apt).

1.  First, update the package lists:
    ```bash
    sudo apt update
    sudo apt upgrade
    ```
  <br><br>
2.  **To install Gnome (standard for Ubuntu):**
    ```bash
    sudo apt install ubuntu-desktop
    # or the minimal version:
    sudo apt install ubuntu-gnome-desktop
    ```
    <br><br>
3.  **To install KDE (Kubuntu):**
    ```bash
    sudo apt install kubuntu-desktop
    # or the standard KDE Plasma version:
    sudo apt install kde-plasma-desktop
    ```
    <br><br>
*You can also use the `tasksel` utility (command `sudo tasksel`), where you can check the required environments.*

### 2.5. Characteristics of graphical interfaces (Variant 23: Gnome and JWM)

#### 1. Gnome (GNU Network Object Model Environment)
* **Type:** Full-featured Desktop Environment.
* **General description:** This is one of the most popular graphical environments in the Linux world. It is used by default in well-known distributions such as Ubuntu, Fedora, and Debian.
* **Features:**
    * It has a modern, minimalistic design focused on productivity and simplicity (no unnecessary icons on the desktop).
    * Based on its own GTK+ libraries.
    * Requires 3D graphics acceleration.
    * **Resource consumption:** Relatively high (requires a modern processor and sufficient RAM), so it is not recommended for old hardware.

#### 2. JWM (Joe's Window Manager)
* **Type:** Window Manager.
* **General description:** This is a very lightweight and fast window manager for the X Window System, written in pure C. It is often used in portable distributions, such as Puppy Linux.
* **Features:**
    * Uses a minimum of external libraries, ensuring instant operation even on very weak PCs.
    * Has a classic interface (taskbar at the bottom, system tray, start menu), similar to older versions of Windows (95/98).
    * Configuration is done by editing text XML files, not through graphical menus.
    * **Resource consumption:** Minimal, works even on computers with 256 MB of RAM.
 

## 3. Control questions

**1. Compare Type 1 and Type 2 hypervisors; what is the difference between them and their scope of application?**
* **Type 1 (Bare-Metal):** Installed directly on the hardware ("bare metal") without a host OS. It has direct access to resources.
    * *Scope of application:* Servers, data centers, cloud computing (Enterprise level).
* **Type 2 (Hosted):** Runs as a regular program on top of the main operating system (Windows, Linux, macOS).
    * *Scope of application:* Home PCs, education, software testing, development.
* **Main difference:** Type 1 is more performant and reliable, Type 2 is easier to configure.

**2. Explain the concept of "GNU GPL", what is its main concept?**
**GNU GPL (General Public License)** — is a license for free software. Its main concept is **Copyleft**. This means that any derivative work created based on code under GPL must also be distributed under the same free license. It guarantees users 4 freedoms: to run the program, to study its code, to distribute copies, and to publish improvements.

**3. What is the essence of Open Source software?**
The essence of **Open Source** is that the source code of the program is available for anyone to view. This ensures transparency (one can check for the absence of "spyware"), security (the community quickly finds and fixes vulnerabilities), and independence from a specific manufacturer (no Vendor lock-in).

**4. What is a distribution? (*)**
A **Linux Distribution** — is a ready-to-use software kit that includes: the Linux kernel, system libraries and GNU utilities, a package management system, a graphical environment, and a set of application programs. Since "pure" Linux is just a kernel, the distribution makes it a full-fledged OS for the user.

**5. What system administration tasks can be implemented based on Linux OS? (*)**
* Managing user accounts and file access rights.
* Configuring networks, routing, and firewalls.
* Managing services and processes (systemd).
* Automating routine tasks (Bash scripts, Cron).
* Deploying web servers, databases, and file storage.
* Monitoring system performance and analyzing logs.

**6. How are Android OS and Linux related? (*)**
Android is built on a modified **Linux kernel**. The kernel is responsible for managing memory, processes, and device drivers. However, Android does not use standard GNU libraries (it uses Bionic instead of glibc) and has its own virtual machine (ART) for running applications, so standard Linux programs do not run directly on it.

**7. Main capabilities and scope of use of Embedded Linux? (**)**
**Embedded Linux** — are OS versions optimized for running on devices with limited resources.
* *Scope of use:* Routers, smart TVs, automotive systems (infotainment), industrial controllers, IoT devices, payment terminals.
* *Capabilities:* Real-time operation, high stability, minimal energy and memory consumption, support for specific processor architectures (ARM, MIPS).

**8. How can you change the Linux boot type: in text mode (level 3) or graphical mode (level 5)? How do CLI and GUI modes differ? (**)**
In modern systems with `systemd`, runlevels are replaced by "targets":
* To set text mode by default (analogous to level 3):
    `sudo systemctl set-default multi-user.target`
* To set graphical mode by default (analogous to level 5):
    `sudo systemctl set-default graphical.target`

**Differences:**
* **CLI (Command Line Interface):** Text interface. Consumes minimum resources, ideal for servers, allows full automation.
* **GUI (Graphical User Interface):** Graphical interface (windows, mouse). User-friendly, visual, but requires significant resources (RAM, GPU).

## 4. Conclusion
In the course of this laboratory work, I familiarized myself with the fundamental principles of virtualization and the architecture of the Linux operating system.

While performing the preparation tasks, I studied the classification of virtual environments and analyzed the differences between **Type 1 (Bare-Metal)** and **Type 2 (Hosted)** hypervisors. Within the framework of my variant (No. 23), I examined the features of the **Xen** hypervisor in detail, studying the concept of paravirtualization and the domain separation architecture (Dom0 and DomU), which allows ensuring high performance close to native.

At the practical stage, I mastered the skills of working with the **Oracle VirtualBox** software. I went through the full cycle of operating system deployment: from creating a virtual machine and configuring hardware limitations (support for 32/64-bit architecture, VT-x/AMD-V activation) to installing the Guest Linux OS in text mode.

I also explored the differences in Linux graphical interfaces. According to my variant, I compared the full-featured **Gnome** desktop environment, which is the standard for modern distributions, and the lightweight **JWM** window manager, focused on maximum resource saving. This gave me an understanding of how the choice of shell affects system performance.

Answering the control questions, I consolidated my knowledge about the **Open Source** philosophy and the **GNU GPL** license, and also sorted out the differences between **CLI** (command line) and **GUI** (graphical interface) modes, learning how to switch boot targets via systemd.

The knowledge obtained allows me to effectively deploy test environments, choose optimal virtualization tools for specific tasks, and administer basic Linux OS parameters.
