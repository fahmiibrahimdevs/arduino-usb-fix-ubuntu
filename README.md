# Fix Arduino USB Not Detected on Ubuntu

This guide helps fix the issue where Arduino is not detected via USB on Ubuntu systems.

## 🛠️ Steps to Fix

1. **Add your user to the `dialout` group:**

   ```bash
   sudo usermod -aG dialout $USER
   ```
   After running the command, reboot your computer to apply the group change.

2. **Remove `brltty` package**

   ```bash
   sudo apt remove brltty -y
   ```
   
3. Check if Arduino is detected
   Run the following command:
   
   ```bash
   ls /dev/ttyUSB*
   ```
   If everything is working, you should see something like:
   ```bash
   /dev/ttyUSB0
   ```

## ℹ️ Why This Works
- The `dialout` group grants permission to access `/dev/ttyUSB*` devices.
- `brltty` is a service for Braille terminals, but it can interfere with USB-serial communication.
- Removing `brltty` and ensuring proper user permissions usually resolves the issue.

## 🧪 Tested on:
- Ubuntu 22.04
- Ubuntu 24.04
