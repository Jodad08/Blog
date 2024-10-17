***
Get started with selfhosting.
***
Article Tree
├── Step 1: Download the Debian ISO
│   ├── Visit the Debian Website
│   ├── Choose the Right Version
│   ├── Select the ISO Image
│   └── Download the ISO
│
├── Step 2: Create a Bootable USB Drive
│   ├── Using Rufus (Windows)
│   │   ├── Download Rufus
│   │   ├── Run Rufus
│   │   ├── Select the USB Drive
│   │   ├── Select the ISO
│   │   └── Start the Process
│   │
│   ├── Using Etcher (Windows/Linux/macOS)
│   │   ├── Download Etcher
│   │   ├── Run Etcher
│   │   ├── Select the USB Drive
│   │   └── Flash the Drive
│   │
│   └── Using `dd` (Linux)
│       ├── Identify the USB Drive
│       ├── Unmount the USB Drive
│       ├── Create the Bootable USB
│       └── Sync and Eject
│
├── Step 3: Boot from USB Drive
│   ├── Restart Your Computer
│   ├── Enter BIOS/UEFI Settings
│   ├── Change Boot Order
│   └── Save and Exit
│
├── Step 4: Install Debian
│   ├── Start the Installer
│   ├── Select Language
│   ├── Select Location
│   ├── Configure Keyboard
│   ├── Configure Network
│   ├── Set Up Users and Passwords
│   ├── Partition Disks
│   ├── Select Software
│   ├── Install the GRUB Bootloader
│   └── Finish Installation
│
├── Step 5: First Boot and Configuration
│   ├── Boot into Debian
│   ├── Log In
│   └── Update the System
│
└── Set Up Docker and Portainer
    ├── 1. Install and Set Up a User on Debian
    │   ├── Create a New User
    │   ├── Install `sudo`
    │   ├── Add User to Sudo Group
    │   └── Add User to Docker Group
    │
    ├── 2. Setting Up Docker
    │   ├── Update Package Index
    │   ├── Install Required Packages
    │   ├── Add Docker’s Official GPG Key
    │   ├── Add Docker Repository
    │   ├── Install Docker
    │   └── Verify Docker Installation
    │
    ├── 3. Setting Up Portainer
    │   ├── Create a Docker Volume for Portainer
    │   ├── Run the Portainer Container
    │   └── Access Portainer


# Setting Up a User and Docker Environment on Debian
## 1. Installing and Setting Up a User on Debian

First, you need to install Debian, then you need to create a new user on your Debian system. This can be helpful for managing permissions and keeping your Docker environment organized.
## Step 1: Download the Debian ISO

1. **Visit the Debian Website:**
   - Go to the official Debian website: [Debian Downloads](https://www.debian.org/distrib/).

2. **Choose the Right Version:**
   - Click on "Download an ISO image" and choose the version you want (Stable is recommended for most users).

3. **Select the ISO Image:**
   - For standard installations, select the “amd64” architecture if you're installing on a 64-bit machine.
   - Choose the “netinst” (network installation) ISO for a smaller download, or a full DVD ISO for a complete installation without network dependencies.

4. **Download the ISO:**
   - Click on one of the download links to start downloading the ISO file.

## Step 2: Create a Bootable USB Drive

You need to create a bootable USB drive from the ISO file. You can use tools like Rufus (Windows), Etcher (Windows/Linux/macOS), or the `dd` command (Linux).

### Using Rufus (Windows):

1. **Download Rufus:**
   - Download Rufus from [Rufus's website](https://rufus.ie/).

2. **Run Rufus:**
   - Insert your USB drive and open Rufus.

3. **Select the USB Drive:**
   - Choose your USB drive under "Device."

4. **Select the ISO:**
   - Click on "Select" and choose the downloaded Debian ISO file.

5. **Start the Process:**
   - Click "Start" and confirm any prompts to format the USB drive. Wait for the process to complete.

### Using Etcher (Windows/Linux/macOS):

1. **Download Etcher:**
   - Download Etcher from [Etcher's website](https://www.balena.io/etcher/).

2. **Run Etcher:**
   - Open Etcher and select the Debian ISO file.

3. **Select the USB Drive:**
   - Choose your USB drive.

4. **Flash the Drive:**
   - Click "Flash!" and wait for the process to finish.

### Using `dd` (Linux):

1. **Identify the USB Drive:**
   - Run `lsblk` to find your USB drive (e.g., `/dev/sdX`, where `X` is your drive letter).

2. **Unmount the USB Drive:**
   ```bash
   sudo umount /dev/sdX1
   ```

3. **Create the Bootable USB:**
   ```bash
   sudo dd if=path_to_your_iso.iso of=/dev/sdX bs=4M status=progress
   ```

4. **Sync and Eject:**
   ```bash
   sudo sync
   ```

## Step 3: Boot from USB Drive

1. **Restart Your Computer:**
   - Insert the USB drive and restart your computer.

2. **Enter BIOS/UEFI Settings:**
   - Press the designated key (often F2, F12, ESC, or DEL) to enter BIOS/UEFI settings.

3. **Change Boot Order:**
   - Set the USB drive as the primary boot device.

4. **Save and Exit:**
   - Save your changes and exit the BIOS/UEFI.

## Step 4: Install Debian

1. **Start the Installer:**
   - Your computer should boot from the USB drive and display the Debian installer menu. Select "Install" or "Graphical Install."

2. **Select Language:**
   - Choose your preferred language and press Enter.

3. **Select Location:**
   - Choose your location (e.g., country) and press Enter.

4. **Configure Keyboard:**
   - Select your keyboard layout and press Enter.

5. **Configure Network:**
   - Choose a hostname for your system and configure the network. If you're using a wired connection, it should automatically detect it.

6. **Set Up Users and Passwords:**
   - Set the root password (if prompted) and create a regular user account.

7. **Partition Disks:**
   - Choose a partitioning method:
     - **Guided - use entire disk** (recommended for beginners).
     - **Manual** (for advanced users).
   - If using guided partitioning, select your disk and confirm the changes.

8. **Select Software:**
   - Choose additional software to install (e.g., Desktop Environment, SSH server). For most users, selecting a Desktop Environment (like GNOME or Xfce) is recommended.

9. **Install the GRUB Bootloader:**
   - Confirm the installation of the GRUB bootloader when prompted. Select the disk where you want to install it (usually your main drive).

10. **Finish Installation:**
    - Once the installation is complete, you will be prompted to remove the installation media (USB drive) and reboot your computer.

## Step 5: First Boot and Configuration

1. **Boot into Debian:**
   - After rebooting, your system should load Debian.

2. **Log In:**
   - Use the root account and password you created during installation to log in.
Open your terminal and execute the following command:

```bash
apt-get install sudo
```
## Step 6: Add the User to the Sudo Group

To allow your new user to run Sudo commands with `sudo`, add them to the Sudo group:

```bash
sudo usermod -aG sudo newusername
```

After executing this command, log out and back in to apply the group changes.

## Step 7: Add the User to the Docker Group

To allow your new user to run Docker commands without `sudo`, add them to the Docker group:

```bash
sudo usermod -aG docker newusername
```

After executing this command, log out and back in to apply the group changes.

***
## Part 2
***
## 2. Setting Up Docker

Now, let’s install Docker on your Debian system.

### Step 1: Update the Package Index

Ensure your package index is up to date:

```bash
sudo apt update
```

### Step 2: Install Required Packages

Install necessary packages for allowing `apt` to use repositories over HTTPS:

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

### Step 3: Add Docker’s Official GPG Key

Add the GPG key for the official Docker repository:

```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
```

### Step 4: Add the Docker Repository

Add the Docker repository to APT sources:

```bash
echo "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list
```

### Step 5: Install Docker

Update the package index again and install Docker:

```bash
sudo apt update
sudo apt install docker-ce
```

### Step 6: Verify Docker Installation

To confirm Docker is installed correctly, run:

```bash
docker --version
```

## 3. Setting Up Portainer

Portainer is a lightweight management UI that allows you to easily manage your Docker containers.
***
[Portainer Docs](https://docs.portainer.io/start/install-ce/server/docker/linux)
***
### Step 1: Create a Docker Volume for Portainer

First, create a volume to persist Portainer’s data:

```bash
docker volume create portainer_data
```

### Step 2: Run the Portainer Container

Now, run the Portainer container using the following command:

```bash
docker run -d -p 9000:9000 --name portainer --restart always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce
```

This command will start Portainer on port 9000.

### Step 3: Access Portainer

Open your web browser and navigate to `http://your-server-ip:9000`. You’ll be prompted to set up an admin account.

***
## PS: Check out my other Docker Guides
***
For the future:
[Arr suite]
[Simple Deezer Downloader]
[Kavita Book]
[Jellyfin]
***
