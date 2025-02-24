# AcerAN515-47LinuxScreenBrightnessIssue
"Fix Acer Nitro and other laptop brightness control issues with this automated systemd service. This Linux script monitors and adjusts brightness using inotify-tools for Intel and Nvidia backlight controls. Easy installation and setup with systemd support. Works on Linux Mint and other distributions. Improve your display brightness control today!"

# Brightness Bypass Service

This project provides a systemd service to bypass brightness control issues on Acer Nitro and other similar laptops using `inotify-tools`.

## Features
- Monitors brightness changes and applies necessary adjustments automatically.
- Uses systemd for automatic startup.
- Supports Intel and Nvidia-based backlight controls.

## Installation

### Prerequisites
Ensure your system has `inotify-tools` installed. The installation script will handle this automatically.

### Steps
1. Clone this repository:
   ```sh
   git clone https://github.com/adithyanhp/AcerAN515-47LinuxScreenBrightnessIssue.git
   cd brightness-bypass
   ```
2. Run the installation script:
   ```sh
   chmod +x install_brightness_bypass.sh
   ./install_brightness_bypass.sh
   ```
3. Open the terminal and edit the GRUB configuration:
   ```sh
   sudo nano /etc/default/grub
   ```
   Replace the line:
   ```sh
   GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
   ```
   with:
   ```sh
   GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=native"
   ```
   Save the file by pressing `CTRL+O`, then `ENTER`, and exit using `CTRL+X`.

4. Update GRUB and reboot:
   ```sh
   sudo update-grub
   reboot
   ```

## Files
- `brightness_bypass.service`: Systemd service file to manage the brightness bypass script.
- `brightness_bypass_service.sh`: The script that monitors brightness changes and applies necessary modifications.
- `install_brightness_bypass.sh`: Installs and configures the brightness bypass service.

## Usage
After installation, the service should start automatically. To manually manage it:

- Start the service:
  ```sh
  sudo systemctl start brightness_bypass.service
  ```
- Stop the service:
  ```sh
  sudo systemctl stop brightness_bypass.service
  ```
- Check the status:
  ```sh
  sudo systemctl status brightness_bypass.service
  ```
- Enable the service on boot:
  ```sh
  sudo systemctl enable brightness_bypass.service
  ```

## Uninstallation
To remove the service, run:
```sh
sudo systemctl stop brightness_bypass.service
sudo systemctl disable brightness_bypass.service
sudo rm /etc/systemd/system/brightness_bypass.service
sudo rm /usr/local/bin/brightness_bypass_service.sh
sudo systemctl daemon-reload
```

## Notes
- This script was primarily tested on Linux Mint but should work on other distributions with similar configurations.
- If you encounter permission issues, ensure you have the appropriate privileges to modify system files.

## Contributing
Pull requests are welcome! If you have suggestions or improvements, feel free to contribute.

## License
This project is licensed under the MIT License.

