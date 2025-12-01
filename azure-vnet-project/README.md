# Azure VNet + Linux VM + NGINX (Cloud Lab)

## Overview
After completing the AZ-900 Exam, I deployed a Linux virtual machine in Azure inside a custom virtual network, secured it with a Network Security Group, and installed the NGINX web server. This project demonstrates basic cloud networking, Linux administration, and web hosting on Azure.

## Architecture

- **Resource group:** `sams-cloud-lab-rg` (Central US)
- **Virtual network:** `sams-cloud-vnet` with default subnet
- **Virtual machine:** `sams-linux-vm` (Ubuntu 22.04 LTS, Standard_B1s)
- **Public IP:** `sams-linux-vm-ip`
- **Network security group:** `sams-linux-vm-nsg` attached to NIC `sams-linux-vm613_z1`
- **Web server:** NGINX running on Ubuntu

## Steps Performed

1. **Created a resource group**
   - Name: `sams-cloud-lab-rg`
   - Region: Central US
   - (used Central Us because the free-tier size `Standard_B1s` and the Ubuntu 22.04 LTS image were not available in East US for my subscription.)


2. **Created a virtual network**
   - Name: `sams-cloud-vnet`
   - Default subnet in Central US region

3. **Deployed a Linux VM**
   - Image: Ubuntu 22.04 LTS
   - Size: `Standard_B1s` (free-tier eligible)
   - Authentication: username/password (`samadmin`)
   - Attached to `sams-cloud-vnet` and default subnet
   - Public IP enabled

4. **Configured network security**
   - NSG: `sams-linux-vm-nsg`
   - Inbound rules:
     - SSH (TCP 22) from Any
     - HTTP (TCP 80) from Any

5. **Connected to the VM via SSH**
   - Powershell
   - ssh samadmin@<public-ip>
   - then bash

6. **Installed and started NGINX**
   - sudo apt update
   - sudo apt install nginx -y
   - sudo systemctl start nginx
   - sudo systemctl enable nginx
7. **Verified the web server**
   - Opened http://IP-Adress in a browser
   - Confirmed the “Welcome to nginx!” page loaded

