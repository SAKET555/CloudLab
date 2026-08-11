# Experiment 1: Install VirtualBox/VMware Workstation with Linux or Windows OS (Detailed Guide)

## Aim
To install and configure a Type-2 hypervisor (Oracle VM VirtualBox or VMware Workstation) on a host operating system, enabling the execution of guest operating systems (various flavors of Linux or Windows).

## Prerequisites
Before beginning the installation, ensure the following requirements are met:
1. **Hardware Virtualization Enabled**: Ensure that Intel VT-x or AMD-V virtualization is enabled in your system's BIOS/UEFI settings.
2. **System Requirements**: 
   - A minimum of 4 GB RAM (8 GB or more recommended).
   - At least 20 GB of free disk space for the guest operating system's virtual disk.
3. **Installer File**: Download the latest stable version of Oracle VM VirtualBox (or VMware Workstation Player) from the official website.

---

## Detailed Step-by-Step Procedure

### 1. Welcome and Setup Initialization
Download the VirtualBox installer executable (`.exe`). Run the installer with administrator privileges. In the welcome wizard screen, click **Next** to begin the configuration.

![Step Screenshot](images/step_image_1.png)

### 2. Custom Setup and Component Selection
Here you can select which VirtualBox application features to install (such as USB support, networking, and Python scripting support) and choose the destination folder. It is recommended to keep the default settings. Click **Next** to proceed.

![Step Screenshot](images/step_image_2.png)

### 3. Shortcut and File Association Settings
Select your preferences for creating shortcuts on the desktop, quick launch bar, and registering file associations (e.g., associating `.vbox` files with VirtualBox). Select **Next**.

![Step Screenshot](images/step_image_3.png)

### 4. Network Interfaces Warning
Installing VirtualBox requires configuring virtual network adapters, which will temporarily reset your host system's network connection. Save any active network transfers or web sessions, and click **Yes** to proceed.

![Step Screenshot](images/step_image_4.png)

### 5. Finalize Installation Config
The installer is now ready to begin copying the program files to your system. Click the **Install** button to start the actual installation process.

![Step Screenshot](images/step_image_5.png)

### 6. Installation Completion
Once the setup process finishes copying files and registers the virtualization drivers, the completion dialog will appear. You can check the box to start VirtualBox immediately and click **Finish**. A shortcut icon will now be available on your desktop.

![Step Screenshot](images/step_image_6.png)

---

## Post-Installation: Creating Your First Virtual Machine (VM)
1. **Launch VirtualBox**: Double-click the VirtualBox desktop shortcut.
2. **Create VM**: Click the **New** button at the top.
3. **Configure VM Settings**:
   - **Name**: Enter a name (e.g., `Ubuntu-VM`).
   - **ISO Image**: Select the path to your downloaded Linux (e.g., Ubuntu `.iso`) or Windows installation media.
   - **Memory**: Allocate at least 2048 MB RAM (or half of your host RAM).
   - **Hard Disk**: Choose "Create a virtual hard disk now" and allocate at least 20 GB dynamically allocated disk space.
4. **Boot**: Select the VM from the list and click **Start** to run the OS installation wizard.

## Results
Oracle VM VirtualBox was successfully installed on the host system. The environment was configured to support virtual machines running guest operating systems, and the installation was verified by launching the VirtualBox Manager.
