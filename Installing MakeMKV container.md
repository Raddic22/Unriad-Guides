# Install MakeMKV via Community Applications on Unraid

MakeMKV is a tool for converting (or “ripping”) Blu-ray and DVD discs into digital files. This guide shows you how to install and configure the **jlesage/MakeMKV** container on Unraid via the Community Applications plugin.

---

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [Step 1: Identify Your Optical Drive (srX and sgY)](#step-1-identify-your-optical-drive-srx-and-sgy)
3. [Step 2: Open the Community Applications Plugin](#step-2-open-the-community-applications-plugin)
4. [Step 3: Install the MakeMKV Container](#step-3-install-the-makemkv-container)
5. [Step 4: Configure the MakeMKV Container](#step-4-configure-the-makemkv-container)
    - [Basic Settings](#basic-settings)
    - [Automatic Disc Ripper Settings](#automatic-disc-ripper-settings)
    - [Device Settings](#device-settings)
6. [Optional Advanced Tips](#optional-advanced-tips)
7. [Final Note](#final-note)

---

## Prerequisites
- An Unraid server (with Community Applications plugin installed).
- A functioning optical drive connected to your Unraid server (Blu-ray or DVD).
- Purchase a valid MakeMKV License Key or use a temporary/trial key from the official MakeMKV website.

---

## Step 1: Identify Your Optical Drive (srX and sgY)
1. **Open the Unraid Terminal** (via the webUI or SSH).
2. Run the following command:
   ```bash
   lsscsi -g
3. Look at the output to identify your optical drive’s device names (srX and sgY).

   Example Output:
   ```bash
   [2:0:0:0]  cd/dvd  HL-DT-ST  BD-RE  BH10LS38  1.00  /dev/sr1  /dev/sg2
- `srX` might be `/dev/sr1`
- `sgY` might be `/dev/sg2`
  > *Note: Your actual device names may differ. Make note of these for later steps.*

---

## Step 2: Open the Community Applications Plugin
1. Log in to your Unraid webUI.
2. Navigate to the Apps tab (Community Applications).
3. Search for jlesage/MakeMKV.

---

## Step 3: Install the MakeMKV Container
1. Find and select the jlesage/MakeMKV container in the search results.
2. Click Install. This will bring you to the configuration page.

---

## Step 4: Configure the MakeMKV Container
### Basic Settings
Most default settings will be fine, but confirm or adjust these options as needed:

- **Name**: `MakeMKV`  
- **Repository**: `jlesage/makemkv`
- **Network Type**: `bridge`  
  > *You can change to `host` or another preferred network type if desired.*
- **Use Tailscale**: `off`
- **Console Shell Command**: `shell`
- **Privileged**: `OFF`  
  > *In most cases this can remain off. If special permissions are required for hardware access, enable with caution.*
- **Storage**:  
  - **Host Path**: `/mnt/user/Storage`  
  - **Container Path**: `/storage`  
  - *Use a location on your host where you want MakeMKV to have read access or where source files will be located.*
- **Output Directory**:  
  - **Host Path**: `/mnt/user/storage/MakeMKV`  
  - **Container Path**: `/output`  
  - *This is where final converted videos will be saved.*
- **License Key**  
- **License Key**  
  - Enter your valid MakeMKV License Key here (purchased or trial).

### Automatic Disc Ripper Settings
These control automatic ripping behavior if you enable the auto-rip feature:

- **Automatic Disc Ripper Enabled**: `0`
- **Automatic Disc Ripper Eject**: `0`
- **Automatic Disc Ripper Parallels**: `0`
- **Automatic Disc Ripper Blu-ray Rip Mode**: `mkv`
- **Automatic Disc Ripper Force Unique Output Directory**: `0`
- **Automatic Disc Ripper Disable Progress in GUI**: `0`

> **Tip**: Change **Automatic Disc Ripper Enabled** to `1` if you want MakeMKV to automatically rip discs when inserted. Adjust other settings accordingly.

### Device Settings
Link your physical optical drives to the container so MakeMKV can access them:

- **Device srX**: `/dev/srX` ([from Step 1](#step-1-identify-your-optical-drive-srx-and-sgy), e.g. `/dev/sr1`)
- **Device sgY**: `/dev/sgY` ([from Step 1](#step-1-identify-your-optical-drive-srx-and-sgy), e.g. `/dev/sg2`)

## Optional Advanced Tips
- **NVIDIA GPU Transcoding**: If you have the Unraid NVIDIA plugin installed, you can pass a compatible GPU to this container for hardware-accelerated video conversion. Refer to the Unraid documentation on how to enable NVIDIA GPU pass-through for Docker containers.
- **Disk Permissions**: If you encounter issues with file or folder permissions, run the `New Permissions` tool from the Unraid webUI or manually set the correct permissions via the terminal.
- **Auto-Updates**: You can configure your container to auto-update by using the Community Applications Auto Update plugin or by manually updating via the Docker tab.

---

## Final Note
Once the container is set up and running, you can access MakeMKV through its webUI:
   ```
   http://<UNRAID_IP>:7806/
```
Replace `<UNRAID_IP>` with the IP address of your Unraid server.

Enjoy your freshly ripped media!


