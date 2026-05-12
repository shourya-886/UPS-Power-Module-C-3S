# UPS-Power-Module-C-3S

## Overview

This guide explains how to install and run the official Waveshare battery monitoring software for the UPS Power Module (C) on NVIDIA Jetson Orin systems.

The UPS module communicates over I2C and provides:
- Battery voltage monitoring
- Current monitoring
- Power monitoring
- Battery percentage estimation

---

## Supported Hardware

### NVIDIA Devices
- NVIDIA Jetson Orin Nano
- NVIDIA Jetson Orin Nano Super
- NVIDIA Jetson Orin NX

### UPS Board
- Waveshare UPS Power Module (C)

---

## Official Resources

### Product Page
https://thinkrobotics.com/products/uninterruptible-power-supply-ups-module-c-for-jetson-orin?variant=51301717442877&country=IN&currency=INR&utm_medium=product_sync&utm_source=google&utm_content=sag_organic&utm_campaign=sag_organic&utm_source=googleads&utm_medium=cpc&gad_source=1&gad_campaignid=23108168791&gbraid=0AAAAACk3EvzPinXjbxXBXzpnKQTyo8_Xe&gclid=Cj0KCQjw37nNBhDkARIsAEBGI8M-4jLxxjAW4BFPMap-iiJHgEcXFXb_87aT9xogb7w4gyNGhaQBR-QaAkvPEALw_wcB

### Wiki
https://www.waveshare.com/wiki/UPS_Power_Module_(C)

### Official ZIP Package
https://files.waveshare.com/wiki/UPS%20Power%20Module%20(C)/UPS_Power_Module_C.zip

---

# Installation Methods

You can install the software using either:
1. Direct ZIP download from Waveshare
2. Git clone from this repository

---

# Method 1 — Install Using Official ZIP File

## 1. Download the Official Package

Open a terminal and run:

```bash
wget "https://files.waveshare.com/wiki/UPS%20Power%20Module%20(C)/UPS_Power_Module_C.zip"
```

---

## 2. Extract the ZIP File

Run:

```bash
unzip UPS_Power_Module_C.zip
```

If `unzip` is not installed:

```bash
sudo apt update
sudo apt install unzip -y
```

---

## 3. Enter the Extracted Directory

Run:

```bash
cd UPS_Power_Module_C
```

Verify the contents:

```bash
ls
```

You should see files similar to:

```text
ina219.py
```

---

# Method 2 — Install Using Git Clone

This repository contains the extracted contents of the official Waveshare ZIP package.

Using Git is recommended for:
- easier updates
- version control
- development workflows
- ROS2 integration

---

## 1. Clone the Repository

Run:

```bash
git clone https://github.com/shourya-886/UPS-Power-Module-C-3S.git
```

---

## 2. Enter the Repository Directory

Run:

```bash
cd UPS-Power-Module-C-3S/UPS_Power_Module_C/
```

---

# Dependency Installation

Install the required I2C and Python packages:

```bash
sudo apt update
sudo apt install python3-smbus i2c-tools -y
```

---

# Running the Battery Monitor

Execute:

```bash
sudo python3 ina219.py
```

The script should display:
- Voltage
- Current
- Power
- Battery percentage

---

# Optional: Run Without sudo

The script accesses `/dev/i2c-*` devices directly.  
By default, normal users may not have permission.

## Add User to the I2C Group

Run:

```bash
sudo usermod -aG i2c $USER
```

Then reboot:

```bash
sudo reboot
```

After reboot, you should be able to run:

```bash
python3 ina219.py
```

without `sudo`.

---

# Verifying I2C Communication

## Detect Connected I2C Devices

Run:

```bash
sudo i2cdetect -y 7
```

If bus `7` does not work, try:

```bash
sudo i2cdetect -y 1
```

You should see an address appear in the grid.

Example:

```text
40: -- 41 -- -- -- -- -- --
```

The UPS module commonly appears at:
- `0x41`

---

# Troubleshooting

## PermissionError: [Errno 13] Permission denied

### Cause
Your user does not have permission to access the I2C device.

### Solution

Run:

```bash
sudo python3 ina219.py
```

Or permanently fix permissions:

```bash
sudo usermod -aG i2c $USER
sudo reboot
```

---

## ModuleNotFoundError: No module named 'smbus'

### Solution

Install the missing package:

```bash
sudo apt install python3-smbus -y
```

---

## Remote I/O Error

### Possible Causes
- UPS board not connected properly
- Incorrect I2C bus number
- Loose pogo-pin connection
- Incorrect I2C address
- Board not powered

### Recommended Check

```bash
sudo i2cdetect -y 7
```

---

## Empty I2C Detection Table

### Possible Causes
- Hardware connection issue
- Wrong I2C bus
- UPS board not powered

Verify:
- Battery installation
- Pogo-pin alignment
- Power LEDs
- Jetson power state

---

# File Structure

Example directory structure:

```text
UPS_Power_Module_C/
├── ina219.py
├── README.md
└── ...
```

---
