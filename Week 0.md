# Week 0 – System Setup & Tool Installation

## Overview
This document covers the complete setup process for Digital VLSI SoC Design tools, including system requirement verification, virtualization setup, and essential tool installation.

---

## 1. System Requirement Check (Windows)

Before installing Ubuntu, I checked my system configuration using **PowerShell** commands:

### RAM Check
```powershell
Get-ComputerInfo | Select-Object CsTotalPhysicalMemory
```

**Output:** ~8 GB

![PowerShell RAM Check](screenshots/powershell-outputs/ram-check.png)

---

### CPU (Logical Processors) Check
```powershell
Get-ComputerInfo | Select-Object CsNumberOfLogicalProcessors
```

**Output:** 8 CPUs



### Disk Space Check
```powershell
Get-PSDrive C
```

**Output:** 144 GB free


---

### Operating System Check
```powershell
Get-ComputerInfo | Select-Object OsName, OsVersion
```

**Output:** Windows 11 Home

<img width="660" height="427" alt="image" src="https://github.com/user-attachments/assets/4f12d5b6-da2e-4714-8112-b36c821ca1e4" />


### System Requirements Verification

| Requirement | Minimum | My System | Status |
|-------------|---------|-----------|--------|
| RAM | ≥ 6 GB | 8 GB | ✅ Pass |
| Disk Space | ≥ 50 GB | 144 GB | ✅ Pass |
| CPU Cores | ≥ 4 vCPU | 8 CPUs | ✅ Pass |
| OS | Windows 10/11 | Windows 11 | ✅ Pass |


---

## 2. Installing VirtualBox

### Download and Installation
* Downloaded **Oracle VirtualBox** from: [VirtualBox Downloads](https://www.virtualbox.org/wiki/Downloads)
* Installed VirtualBox with default settings
<img width="660" height="483" alt="image" src="https://github.com/user-attachments/assets/553d9442-f50e-4f6e-8c77-f88f6af13a3a" />


---

## 3. Installing Ubuntu 20.04 on VirtualBox

### Ubuntu ISO Download
* Downloaded **Ubuntu 20.04.6 Desktop ISO** from: [Ubuntu ISO](https://releases.ubuntu.com/20.04/)

### Virtual Machine Configuration
Created new VM in VirtualBox with the following configuration:

| Setting | Value |
|---------|-------|
| Name | Ubuntu-VLSI-Design |
| RAM | 4096 MB (4 GB) |
| CPUs | 4 cores |
| Disk Size | 50 GB (Dynamic) |
| Graphics | 128 MB |

<img width="979" height="545" alt="image" src="https://github.com/user-attachments/assets/66b4db07-8fca-4df1-b4d5-4e09881ce3a7" />


---

### Ubuntu Installation Process
* Attached Ubuntu ISO to VM
* Booted VM and started installation
* Selected minimal installation
* Skipped online accounts & upgrade (to save time)

<img width="979" height="551" alt="image" src="https://github.com/user-attachments/assets/0742e825-7a2b-4b92-b90e-906640891363" />

---

## 4. Installing Tools on Ubuntu

After successfully booting into Ubuntu, opened terminal using **Ctrl+Alt+T** and proceeded with tool installation:

### System Update
```bash
sudo apt update
sudo apt upgrade -y
```
<img width="979" height="751" alt="image" src="https://github.com/user-attachments/assets/bb2164c9-3149-49c5-9a64-7792799767e4" />


---

### Installing Dependencies
```bash
sudo apt install git build-essential clang bison flex libreadline-dev gawk \
tcl-dev libffi-dev graphviz xdot pkg-config python3 libboost-system-dev \
libboost-python-dev libboost-filesystem-dev zlib1g-dev -y
```

---

### Installing Iverilog & GTKWave
```bash
sudo apt install iverilog gtkwave -y
```
<img width="979" height="751" alt="image" src="https://github.com/user-attachments/assets/fcd4b3f5-68be-4b29-a0ef-c7dee663ade8" />



---

### Installing Yosys
```bash
git clone https://github.com/YosysHQ/yosys.git
cd yosys
make config-gcc
make
sudo make install
```
<img width="979" height="761" alt="image" src="https://github.com/user-attachments/assets/b0a22a4c-8f7b-4e9b-8179-dd899d13cbe9" />

---

## 5. Tool Verification

### Yosys Version Check
```bash
yosys -V
```

![Yosys Version](screenshots/verification/yosys-version.png)

---

### Iverilog Version Check
```bash
iverilog -v
```

![Iverilog Version](screenshots/verification/iverilog-version.png)

---

### GTKWave Version Check
```bash
gtkwave --version
```

![GTKWave Version](screenshots/verification/gtkwave-version.png)

---

### All Tools Verification Summary
```bash
# Quick verification script
echo "=== VLSI Tools Verification ==="
echo "Yosys Version:"
yosys -V
echo -e "\nIverilog Version:"
iverilog -v
echo -e "\nGTKWave Version:"
gtkwave --version
echo "=== All Tools Installed Successfully ==="
```

---

## 6. Installation Summary

### Completed Tasks

- [x] **System Requirements Check** - Verified Windows system meets minimum requirements
- [x] **VirtualBox Installation** - Successfully installed Oracle VirtualBox
- [x] **Ubuntu 20.04 Setup** - Created and configured VM with Ubuntu 20.04.6 LTS
- [x] **Tool Installation** - Installed all required VLSI design tools:
  - [x] **Yosys** - Logic synthesis tool
  - [x] **Iverilog** - Verilog simulator
  - [x] **GTKWave** - Waveform viewer
- [x] **Tool Verification** - Confirmed all tools are working properly

### Installed Tool Versions

| Tool | Version | Purpose |
|------|---------|---------|
| VirtualBox | 7.0.x | Virtualization Platform |
| Ubuntu | 20.04.6 LTS | Development Environment |
| Yosys | Latest | Logic Synthesis |
| Iverilog | 11.0+ | Verilog Simulation |
| GTKWave | 3.3.x+ | Waveform Analysis |

### System Resources Used

| Resource | Allocated | Used |
|----------|-----------|------|
| VM RAM | 4 GB | ~2-3 GB |
| VM Storage | 50 GB | ~25 GB |
| Host RAM | 8 GB Total | ~6 GB Available |
| Host Storage | 144 GB Free | ~25 GB Used |

---

✅ **Week 0 Complete** - System setup and tool installation finished successfully!

