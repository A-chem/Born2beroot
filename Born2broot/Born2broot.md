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
##  Creating sudo.log

1. Limit Authentication Attempts to 3. Open the sudoers file using `sudo visudo` and Add or modify the following line `Defaults        passwd_tries=3`
2. Display a Custom Error Message for Wrong Password In the same `sudoers` file, add or modify `Defaults badpass_message="Your custom error message here"`
3. Archive sudo Actions in /var/log/sudo To log all sudo activities (both inputs and outputs) in a specific directory `sudo mkdir -p /var/log/sudo` and `sudo chmod 700 /var/log/sudo` In the `sudoers` file, add or modify : `Defaults log_input`  `Defaults log_output`  `Defaults iolog_dir=/var/log/sudo`
- `log_input`: Archives the commands run using `sudo`.
- `log_output`: Archives the output of those commands.
- `iolog_dir`: Specifies the directory where logs are saved.
4.  Enable [[TTY]] Mode for Security. Enabling TTY ensures sudo commands can only be run from a terminal session, adding an extra layer of security. Add or modify the following line in the `sudoers` file: `Defaults        requiretty`
5. Restrict Paths for sudo. Restricting paths ensures users can only execute commands located in approved directories, reducing potential misuse.Add or modify the following line in the `sudoers` file: - `Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"`
## Installing Git and Vim

1. Then type `apt-get install git -y` to install Git
2. Then type `git --version` to check the Git Version
1. Then type `apt-get install vim -y` to install Vim
2. Then type `vim --version` to check the Vim Version
## Installing & Configuring [[SSH (Secure Shell Host)]]

1. Type `sudo apt install openssh-server`
2. verify ssh installation `dpkg -l | grep openssh-server`
3. Type `sudo systemctl status ssh` to check SSH Server Status
4. Type `sudo vim /etc/ssh/sshd_config`
5. Find this line `#Port22`
6. Change the line to `Port 4242` without the # (Hash) in front of it  and disable root login `PermitRootLogin no` if y want restrict SSH access to specific users(Optional, but recommended) `AllowUsers your_username`
7. Restart the SSH service to apply changes `sudo systemctl restart sshd`
8. Check if SSH is running on the correct port: `sudo ss -tuln | grep 4242` You should see something like: `LISTEN 0 128 0.0.0.0:4242 0.0.0.0:*`
9. Then type `sudo grep Port /etc/ssh/sshd_config` to check if the port settings are right
10. Use a second terminal or another machine to test `ssh your_username@your_vm_ip -p 4242` and You should not be able to connect as root `ssh root@your_vm_ip -p 4242`This should fail with a message like: - `Permission denied (publickey, password).`
##  Installing & Configuring [[UFW (Uncomplicated Firewall)]]

1. First type `apt-get install ufw` to install UFW
2. verify ssh installation  `dpkg -l | grep ufw`
3. Type `sudo ufw enable` to inable UFW
4. Type `sudo ufw status numbered`  or `sudo systemctl status ufw` to check the status of UFW
5. Type `sudo ufw allow ssh` to configure the Rules
6. Type `sudo ufw allow 4242` to configure the Port Rules
7. Lastly Type `sudo ufw status numbered` to check the status of UFW 4242 Port

## Connecting to SSH

0. Go to your Virtual Box Program
1. Click on your Virtual Machine and select `Settings`
2. Click `Network` then `Adapter 1` then `Advanced` and then click on `Port Forwarding`
3. Change the Host Port and Guest Port to `4242`
4. Type `sudo systemctl restart ssh` to restart your SSH Server
5. Type `sudo service sshd status` to check your SSH Status
6. Open an iTerm and type the following `ssh your_username@127.0.0.1 -p 4242`

## User Management

### Step 1: Modify the Hostname

 1. Change the hostname to your login followed by `42` use command `sudo hostnamectl set-hostname wil42`. Verify the change : `hostnamectl`
### Step 2: Implement the Strong Password Policy

To implement the password policy, you need to modify the `/etc/login.defs` file and set password aging rules, as well as configure `pam_pwquality.so` for password strength.

1. Set Password Aging Rules. Edit `/etc/login.defs` to configure password expiration and minimum password change settings: `sudo nano /etc/login.defs` and Add or modify the following lines:

- `PASS_MAX_DAYS   30       # Maximum days before password expires`
- `PASS_MIN_DAYS   2        # Minimum days before password can be changed`
- `PASS_WARN_AGE   7        # Number of days before expiry to warn user`

2. `sudo apt-get install libpam-pwquality` to install Password Quality Checking Library
3. Configure Password Complexity. Edit `/etc/pam.d/common-password`. Add the following line :`password requisite pam_pwquality.so retry=3 minlen=10 ucredit=-1 lcredit=-1 dcredit=-1 maxrepeat=3 reject_username difok=7 enforce_for_root`
4. Check the password expiration date using the `chage` command:`sudo chage -l testuser`

### Step 3:Create the User with Your Login as Username &Create group user42

To create a user with your login name (e.g., `wil42`) and make sure they belong to both the `user42` and `sudo` groups:
1. Create the user: `sudo useradd wil42`
2. Set a password for the user: `sudo passwd wil42`
3. Add the user to the `user42` and `sudo` groups: `sudo usermod -aG user42,sudo wil42`
4. Verify group membership: `groups wil42`
5. Create a new group  `sudo groupadd groupname`
##  [[Crontab]] Configuation


is a background process manager. The specified processes will be executed at the time you specify in the crontab file.

1. Then type `apt-get install -y net-tools` to install the netstat tools
2. Then type `cd /usr/local/bin/`
3. Then type `touch monitoring.sh`
4. Lastly type `chmod 777 monitoring.sh` 
5. we must edit the crontab file `sudo crontab -u root -e`
6. In the file, we must add the following command for the script to execute every 10 minutes `*/10 * * * * sh /path_to_file.sh`

`#!/bin/bash`

`Get system architecture and kernel version`
`architecture=$(uname -m)`
`kernel_version=$(uname -r)`

`Get the number of physical and virtual processors`
`physical_processors=$(nproc --all)`
`virtual_processors=$(lscpu | grep "^CPU(s):" | awk '{print $2}')`

`Get memory usage`
`ram_usage=$(free -h | grep Mem | awk '{print $3 "/" $2 " (" $3/$2*100 "%)"}')`

`Get disk usage`
`disk_usage=$(df -h | grep '^/dev/' | awk '{print $3 "/" $2 " (" $5 ")"}')`

`Get CPU load`
`cpu_load=$(top -bn1 | grep "Cpu(s)" | sed "s/.*, *\([0-9.]*\)%* id.*/\1/" | awk '{print 100 - $1 "%"}')`

`Get last reboot time`
`last_reboot=$(who -b | awk '{print $3, $4}')`

 `Check if LVM is active`
`lvm_status=$(lsblk | grep -q "lvm" && echo "Yes" || echo "No")`

 `Get active connections`
`active_connections=$(ss -tuln | grep -c 'ESTAB')`

`Get the number of logged-in users`
`logged_in_users=$(who | wc -l)`

`Get IP and MAC addresses`
`ip_address=$(hostname -I | awk '{print $1}')`
`mac_address=$(cat /sys/class/net/eth0/address)`

`Get the number of sudo commands executed`
`sudo_count=$(grep -c 'sudo' /var/log/auth.log)`

 `Combine everything into a message`
`message="`
`Architecture: $architecture`
`Kernel: $kernel_version`
`Physical CPUs: $physical_processors`
`vCPUs: $virtual_processors`
`Memory Usage: $ram_usage`
`Disk Usage: $disk_usage`
`CPU Load: $cpu_load`
`Last Boot: $last_reboot`
`LVM Active: $lvm_status`
`Active Connections: $active_connections`
`Logged-in Users: $logged_in_users`
`IP: $ip_address (MAC: $mac_address)`
`Sudo Commands: $sudo_count`
`"`

`Display the message on all terminals`
`echo "$message" | wall`

# BONUS SERVICES
## Install [[Lighttpd]]

1. `sudo apt install lighttpd 
2. start and enable the Lighttpd service: `sudo systemctl start lighttpd`
3. We allow connections through port 80 with the command: `sudo ufw allow 80`
4. We check that we have actually allowed it. Port 80 and allow should appear: `sudo ufw status`
5. To install the latest version of [[WordPress]] we must first install wget and zip. To do this we will use the following command: `sudo apt install wget zip` 
6. locate ourselves in the folder /var/www/ with the command : `cd /var/www/` download the latest version of WordPress `sudo wget` https://es.wordpress.org/latest-es_ES.zip 
7. 1. Unzip the file you just downloaded with the command: `sudo unzip latest-en_US.zip`