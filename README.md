# UPS-Power-Module-C-3S
This repo contains the zip file for the Waveshare UPS Power Module (C) 3S. The module has 3x21700 battery slots... THIS IS NOT A OFFICIAL REPO
THIS CODE IS NOT TESTED ON WINDOWS, ONLY ON UBUNTU 22.04 LTS

Follow the given instructions to install it:

1. Just clone this repo on your Jetson Orin Nano/NX by running the command in the terminal/Command prompt/ PowerShell
     ```
     git clone https://github.com/shourya-886/UPS-Power-Module-C-3S.git
     ```
2. Moving into the cloned folder
   ```
   cd UPS-Power-Module-C-3S-main/UPS_Power_Module_C
   ```
3.  Installing dependencies
   ```
     sudo apt update
     sudo apt install python3-smbus i2c-tools -y
   ```
4. Running the main code:
   ```
   python3 INA219.py
   ```
