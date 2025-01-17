# Install MakeMKV via Community Applications

## Step 1: Obtain Optical Drive srX and sgY
1. Open the Unraid Terminal.
2. Enter the following command into the terminal:
   ```bash
   lsscsi -g
   ```
3. Note down the `srX` and `sgY` of your optical drive.

   Example output:
   ```
   [2:0:0:0]  cd/dvd  HL-DT-ST  BD-RE  BH10LS38  1.00  /dev/sr1  /dev/sg2
   ```
   In this example:
   - `srX` is `/dev/sr1`
   - `sgY` is `/dev/sg2`

   Your values may differ. Replace `srX` and `sgY` in later steps accordingly.

---

## Step 2: Open the Community Applications Plugin
1. Log in to your Unraid WebUI.
2. Navigate to the **Apps** tab (Community Applications).
3. Use the search bar to search for `jlesage/MakeMKV`.

---

## Step 3: Install the MakeMKV Container
1. In the search results, select the `jlesage/MakeMKV` container.
2. Click **Install** to proceed to the configuration page.

---

## Step 4: Configure the MakeMKV Container
Most settings will remain with the default configuration.

- **Name**: `MakeMKV`
- **Additional Requirements**: *None Listed*
- **Repository**: `jlesage/makemkv`
- **Network Type**: `bridge` (This can be changed to your preferred network type)
- **Use Tailscale**: `OFF`
- **Console Shell Command**: `shell`
- **Privileged**: `OFF`
- **Storage**: `/mnt/user/Storage`  
  This location contains files from your host that need to be accessible by the application.  
  **Container Path**: `/storage`
- **Output Directory**: `/mnt/user/storage/MakeMKV`  
  This is the default output folder for converted videos.  
  **Container Path**: `/output`
- **Licence Key**:  
  Enter your MakeMKV Licence Key here. You should receive this when purchasing MakeMKV.

### Automatic Disc Ripper Settings
- **Automatic Disc Ripper Enabled**: `0`
- **Automatic Disc Ripper Eject**: `0`
- **Automatic Disc Ripper Parallel**: `0`
- **Automatic Disc Ripper Blu-ray Rip Mode**: `mkv`
- **Automatic Disc Ripper Force Unique Output Directory**: `0`
- **Automatic Disc Ripper Disable Progress in GUI**: `0`

### Device Settings
- **Device srX**: `/dev/srX` (Obtained from Step 1, e.g., `/dev/sr1`)
- **Device sgY**: `/dev/sgY` (Obtained from Step 1, e.g., `/dev/sg2`)

---

## Final Note
Once the container is set up and running, you can access MakeMKV through its web interface and start converting your optical media.
