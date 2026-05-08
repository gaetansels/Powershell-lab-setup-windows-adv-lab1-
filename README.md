# Powershell-lab-setup-windows-adv-lab1-
## Overview
In this lab, I'm setting up a Server Core environment that will be operated via CLI and PowerShell, connected to a GUI client for remote management.

## Lab Objectives

### Server Core Setup
- Install **Windows Server 2025** as Server Core on a new VM
- Configure a static IP address within the 192.168.153.0/24 subnet
- Assign a new hostname to the server
- Install a new forest on the server: **LOCAL.TEST**

### Client Configuration
- Add a new client to the domain for management tasks:
  - Assign proper hostname
  - Configure static IP address
  - Join the domain
- Install **RSAT modules** for remote server management
- Create a new MMC console with **Active Directory Users and Computers** module
- Connect to Core server via **PowerShell Remoting (WinRM)**
- Add an additional client for testing purposes

### User Management
- Create a standard user account for daily use
- Create a separate **Domain Admin** account for administrative tasks

### PowerShell Exercises
- Retrieve all running services
- Display the first 5 running services
- Show all data from Word and PowerPoint processes (with documents open)
- List IPv4 addresses on localhost in table format sorted by interface index
- Display 5 properties of local disk in table format

## Technologies Used
- Windows Server 2025 Core
- Active Directory Domain Services
- PowerShell Remoting
- RSAT Tools
- MMC Console


---
*Note: This lab is part of the Graduaat Systeem- en Netwerkbeheer (Course: Windows Server Advanced) at Howest Brugge.
