# Virtualization

**Virtualization** is the process of creating a virtual version of something, like a computer, server, or storage, instead of using physical hardware. It allows one physical machine to act like multiple separate machines.
# What is a Virtual Machine

A **Virtual Machine (VM)** is a software-based computer that runs inside a real, physical computer. It acts like a separate computer, with its own operating system (OS), applications, and resources, but it is virtual instead of physical.
(VM) works by using a [[Hypervisor]]to create a simulated environment that behaves like a physical computer.
# How do Virtual Machines work?
A **Virtual Machine (VM)** works by using a software layer called a [[Hypervisor]], which allows your physical computer to create and run virtual computers. The [[Hypervisor]] divides the hardware resources, such as CPU, memory, and storage, into isolated parts, and assigns these resources to one or more VMs. Each VM acts like a separate computer, with its own [[Operating Oystem]] and applications, even though it’s running on the same physical machine.
# The basic differences between Rocky and Debian

- **Rocky Linux** is based on **Red Hat** and designed for **servers** and **businesses**. It’s stable, long-term, and works well in enterprise environments. It uses **RPM** packages and **YUM** for managing software.
    
- **Debian** is a **general-purpose** Linux that can be used on **desktops** and **servers**. It’s known for its stability and open-source nature. It uses **DEB** packages and **APT** for managing software.
# The purpose of virtual machines

- **Run Different Operating Systems**: For example, run Windows on a Mac or Linux on Windows.
- **Test Software**: Safely test new software or configurations without risking your main system.
- **Save Resources**: Use one physical machine to run many virtual computers, saving space and cost.
- **Isolation**: Keep each virtual machine separate so that problems in one don't affect others.
#  Apt vs Aptitude?

## Debian(package management system)

Is a Linux-based operating system built around packages. Nearly everything in Debian is delivered as a [[Package(.deb)]].
- The kernel (core of the OS) is a package.
- Applications like Firefox.... Player are packages.
- Even system utilities like bash (the shell)...are distributed as packages.

**Managing software manually can be messy :**

1. Find the software online.
2. Download it.
3. Ensure it’s compatible with your system.
4. Check for and install additional required software ([[Dependencies]]).

**Package Management :**

1. Finds the software you want from a [[Repository]].
2. Downloads the correct package version for your system.
3. Installs the package along with any required dependencies.
4. Keeps track of everything so you can easily upgrade or remove software.

### Tools 
#### DPKG (Debian Package)

The low-level tool that installs .deb files directly. It doesn’t resolve dependencies automatically. If the software needs another package to work, you must install that package manually.

**Command**: `sudo dpkg -i <package_name>.deb`
#### APT (Advanced Package Tool)

A higher-level tool that works with repositories. It automatically resolves and installs dependencies. It comes by default and doesn't offer a graphical interface to manage the tools that are installed and the ones that you can need in the future. Apt command offers a lot of sub-commands that help you to manage your system so that the packages can be added, updated, removed, or fixed if a problem occurs. 

**Command**: `sudo apt install <package_name>`

### Aptitude(Advanced Package Tool)
Is another popular tool that you can use over apt the possibility to manage your packages through command lines and also from a visual interface directly on your terminal. When facing a package conflict, `apt` will not fix the issue while `aptitude` will suggest a resolution that can do the job.

**Command**: `sudo aptitude install <package_name>
[[Aptitude.png]]

# APPArmor

Is a Linux security module that enhances system security by restricting what resources an application can access.Instead of relying solely on user and group permissions (Discretionary Access Control or DAC), AppArmor uses Mandatory Access Control (MAC), where system administrators can define what files, capabilities, and other resources an application is allowed to use, regardless of user permissions.

**Check if AppArmor is installed :** `sudo aa-status`

**If it’s not installed :** `sudo apt install apparmor apparmor-utils`

# Configure locals

1. We will choose the version without graphic interface.
2. Now language must be choosed for the machine.
3. It's time to select the country.
4. Time to select continent.
5. Now select the country.
6. Our keyboard follows the ANSI standard so `American English`.
# Configure the network

1. Now we must set a `Host Name` of the machine `achemlal42`
# Set up users and passwords

1. set a password for the root user `Rootuser12`
2. set up the user name, the name for that user have to be your student login `achemlal`
3. set our new user password `Abdilah123`
# Configure the clock

1. Select your time zone.

# BONUS: Partition Disks

**Partitioning a disk** refers to dividing a physical storage device, such as a hard drive (HDD) or solid-state drive (SSD), into multiple logical sections called **partitions**. Each partition acts as a separate unit of storage, allowing the system to manage different data independently.

1. When choosing disk partitioning, we will select manual.
[[image (1).png]]

2. it shows us a general description of our partitions and mount points. Currently, we do not have any partitions. To create a new partition table, we must choose the device where we want to create them. 
[[image(2).png]]

3. it shows us a general description of our partitions and mount points. Currently, we do not have any partitions. To create a new partition table.
[[image (9).png]]

## Types of Partitions:

- **Primary Partitions**: These are the main partitions where the OS and data can be stored. A disk can have up to four primary partitions. . There can only be 4 primary partitions per hard drive or 3 primary and one extended.

-  **Extended Partition**: A type of partition that acts as a container for multiple logical partitions, allowing more than four partitions on a disk.

- **Logical Partitions**: Created inside an extended partition, logical partitions allow you to have more than four partitions.

We will start by creating this:
[[image (4).png]]
# BONUS: primary partition

1. We will create a new partition.
2. he size of the partition must be `525m`
3. We choose primary because it will be the partition where the Operating System will be installed.
4. We will select beginning because we want the new partition to be created at the `beginning` of the available space.
5. We will modify the [[Mount Point]] as specified in the subject. We choose [[boot]] as the mount point for our partition.
[[image(5).png]]
# BONUS: logical partition

1. We will start creating this:
[[image (6).png]]
2. create a logical partition `(Physical volume)` with all the available space `max` on the disk, which has no mount point and is encrypted.
3. create the encrypted volumes `/dev/sda5` password `1234`
# BONUS: logical volume manager

**logical volume management([[LVM]]):**** is a system for managing disk storage in Linux. It allows you to combine multiple physical disks into one or more logical volumes (virtualized storage), which can then be used like a single partition.
  
1. We will create a new volume group.
2. We will enter the name we want to give it. `LVMGroup`
3. select the partition where we want to create the group  `/dev/mapper/sda5_crypt`.
4. Create logical volume.
[[image (8).png]]
5. start by choosing the group where we want them to be created.

| LVs     | Size   |
| ------- | ------ |
| root    | 10.7GB |
| swap    | 2.5GB  |
| home    | 5.4GB  |
| var     | 3.2GB  |
| srv     | 3.2GB  |
| tmp     | 3.2GB  |
| var-log | 4.3GB  |

# BONUS: [[filesystem]] of all logical volumes

1. select the [[filesystem]] (Ext4 journaling file system) that we want and the [[Mount Point]] indicated in the subject .
[[image (9).png]]

| LVs     | Mount Point |
| ------- | ----------- |
| root    | /           |
| swap    | swap        |
| home    | /home       |
| var     | /var        |
| srv     | /srv        |
| tmp     | /tmp        |
| var-log | /var/log    |

# Configure the package manager

1. `No` as is not required additional packages
2. choose `deb.debian.org` as is the recommended by debian itself.

# Install the [[GRUB (Grand Unified Bootloader)]] boot loader

1. install [[GRUB (Grand Unified Bootloader)]] boot in the hard disk
2. choose the device `/dev/sda (ata_VBOX_HARDDISK)` for the installation for boot loader.
3. finish installation

# Starting Your Virtual Machine

1. Press enter on `Debian GNU/Linux`.
2. Enter your encryption password you had created before.
3. Login in as the your_username you had created before.
4. Type `lsblk` in your Virtual Machine to see the partition.

# Configurating Your Virtual Machine
## Installing [[Sudo]]

1. First type `su -` to login in as the root user.
2. Then type `apt install sudo`
3. Verify whether _sudo_ was successfully installed via `dpkg -l | grep sudo`.
4. Add user to _sudo_ group via `adduser <username> sudo` or  `usermod -aG sudo <username>`
5. Verify whether user was successfully added to _sudo_ group via `getent group sudo`.
6. Type `sudo visudo` to open sudoers file
7. Lastly find - # User privilege specification, type `your_username ALL=(ALL) ALL`.
- `your_username`: The user to which you're granting sudo privileges.
- `ALL`: This means the user can run commands from any host (for network configurations).
- `(ALL)`: The user can run commands as any user, including root.
- `ALL`: The user can run any command as root.
9. We must reboot machine so the changes can be applied `sudo reboot`
## Installing Git and Vim

1. Then type `apt-get install git -y` to install Git
2. Then type `git --version` to check the Git Version
1. Then type `apt-get install vim -y` to install Vim
2. Then type `vim --version` to check the Vim Version
## Installing and Configuring [[SSH (Secure Shell Host)]]