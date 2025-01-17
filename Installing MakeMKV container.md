# Install MakeMKV via Community Applications

## Step 1: Obtain optical drive srX and SgY:
1. Login to your Unraid `WebUI`  
2. Open the Unraid Termainl.
3. Enter the following command into the terminal:
    ```
    lsscsi -g  
    ```
4. Note down the srX and sgY of your optiacl drive.

    ``
    eg: [6:0:0:0]  cd/dvd  HL-DT-ST  BD-RE  WH16NS60  1.00  /dev/sr0  /dev/sg3 
    ``

In this example, srX and sgY is `sr1` and `sg2` (Your values may be different).

## Step 2: Open the Community Applications Plugin:
1. Navigate to the `Apps` tab (Community Applications).
2. Use the search bar to search `jlesage/MakeMKV`.

## Step 3: Install the MakeMKV Container:
1. In the search results, select the jlesage/MakeMKV container.
2. Click `Install` to proceed to the configuration page.

## Step 4: Configure the MakeMKV Container (Most will stay with default configuration):
- Name: `MakeMKV`
- Additional Requirements: `None Liste`
- Repository: `jlesage/makemkv`
- Network Type: `Bridge` (This can be changed to your prefered network type)
- Use Tailscale: `OFF`
- Console shell command: `Shell`
- Previleged: `OFF`
- Storage: `/mnt/user/Storage` This location contains files from your host that need to be accessible by the application. Container path: /storage
- Output Directory: `/mnt/user/Storage/MakeMKV` This is the default output folder for converted videos. Also used by the automatic disc ripper. Container path: /output
- Licence Key: `Enter MakeMKV Licence Key Here` You should receive this when purchasing MakeMKV.
- Automatic Disc Ripper: Enabled: `0`
- Automatic Disc Ripper: Eject: `0`
- Automatic Disc Ripper: Parallel: `0`
- Automatic Disc Ripper: Blu-ray Rip Mode: `mkv`
- Automatic Disc Ripper: Force Unique Output Directory: `0`
- Automatic Disc Ripper: Disable Progress in GUI: `0`
- Device srX: `/dev/srX` Obtained from Step 2, in this example it would be `/dev/sr1`.
- Device sgY: `/dev/sgY` Obtained from Step 2, in this example it would be `/dev/sg2`.

