# UPS-Power-Module-C-3S
This repo contains the zip file for the Waveshare UPS Power Module (C) 3S. The module has 3x21700 battery slots... THIS IS NOT A OFFICIAL ZIP FILE

Follow the given instructions to install it:

1. Just clone this repo on your Jetson Orin Nano/NX by running the command in the terminal/Command prompt/ PowerShell
     ```
     wget https://files.waveshare.com/wiki/UPS%20Power%20Module%20(C)/UPS_Power_Module_C.zip
     ```
2. Moving into the cloned folder
   ```
   cd UPS-Power-Module-C-3s
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
