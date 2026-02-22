
### 1. Download the ISO

Visit [massgrave.dev](https://massgrave.dev/windows_arm_links) and select the correct version:

-   **Modern Devices:** Download the latest **Windows 11 Consumer** ISO.
    
-   **Legacy/Unsupported Devices:** Download **Windows 10 IoT Enterprise 22H2**.
    

### 2. Create a Bootable USB

Download [Rufus](https://rufus.ie/en/) and use it to flash the ISO you just downloaded onto a USB drive.

> **Note:** Rufus may warn you about Secure Boot or TPM; adjust these settings based on your specific device's requirements.

### 3. Prepare Drivers

1.  Download the driver archive (e.g., `DEVICE_ID_NAME.7z.001`, `DEVICE_ID_NAME.7z.002`, etc.).
    
2.  Extract the driver files (`.inf`, `.sys`, `.cat`) to a local directory (e.g., `C:\TempDrivers`).
    

### 4. Stage the Image for Modification

Since you cannot modify files directly on a read-only ISO or a slow USB, copy the image to your local drive for faster processing:

-   Copy `U:\sources\install.wim` from your USB to `C:\TempWim\install.wim`.
    

### 5. Mount the Image

Open a **Command Prompt as Administrator** and mount the image to a temporary folder:
```
dism /Mount-Wim /WimFile:C:\TempWim\install.wim /Index:1 /MountDir:C:\TempMount
```

### 6. Inject Drivers

Inject the drivers from your local folder. The `/Recurse` flag ensures all sub-folders are scanned: 
```
dism /Image:C:\TempMount /Add-Driver /Driver:C:\TempDrivers /Recurse
```

### 7. Commit Changes and Unmount

Save the driver injections and close the image: 
```
dism /Unmount-Wim /MountDir:C:\TempMount /Commit
```

### 8. Split the Image (For FAT32 Compatibility)

Windows Setup on many ARM devices requires a FAT32-formatted USB, which cannot handle files larger than 4GB. Split the `.wim` into smaller `.swm` files:
```
dism /Split-Image /ImageFile:C:\TempWim\install.wim /SWMFile:C:\TempWim\install.swm /FileSize:2048
```

### 9. Update the Bootable USB

1.  Navigate to the `\sources\` folder on your **USB drive**.
    
2.  Locate the original `install.wim` and rename it to `install.wim.bak` (to keep it as a backup).
    
3.  Copy all the new `.swm` files (e.g., `install.swm`, `install2.swm`, etc.) from `C:\TempWim\` into the `\sources\` folder on your **USB drive**.
