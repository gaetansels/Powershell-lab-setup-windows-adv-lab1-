
##Server Core Setup

### Context
I have installed Windows Server 2025 as Server Core on a new VM. This server will be promoted to a Domain Controller for the LOCAL.TEST forest.

Below my lab setup : 

![something](images/winadv_lab1_p1.png)

**TASKS:**
- Change Hostname
- Install New role -> AD-Domain-Services + managementtools --> needed to manage the forest 
- Change IP address (IP/SM/DG/DNS)
- update the server after installation --> best practice
- Upgrade server_core to DC in the new forest


##Change Hostname 
`get-help rename-computer -examples` --> this gives examples we can use and adapt to what we need 

`Rename-Computer -NewName "DC1"-Restart`

![something](images/winadv_lab1_p2.png)

*Note:** Omitted `-DomainCredential` parameter as the server is still in a WORKGROUP. This parameter is only needed when renaming domain-joined computers. Local admin rights are sufficient here since no domain exists yet—we're creating it in the next step!


## Install New role -> AD-Domain-Services
`Install-WindowsFeature -name AD-Domain-Services -IncludeManagementTools`

## Change IP address (IP/SM/DG/DNS)

If you want to know which interface you need to install the IP. 

`get-help New-netIPAddress -Examples`--> this gives examples we can use and adapt to what we need 
If there are no examples, we can use  `Update-Help`, make sure to execute it as an administrator. 

`Get-NetAdapter` --> this is how you know the interface card is  (ifIndex)

The following command was used : 
`New-NetIPAddress -InterfaceIndex 6 -IPAddress 192.168.153.200 -PrefixLength 24 -DefaultGateway 192.168.153.254 `

## DNS

`set-DnsClientServerAddress -InterfaceIndex 6 -ServerAddresses ("127.0.0.1")`

![something](images/winadv_lab1_p3.png)

## forest + upgrade to DC

`Install-ADDSForest -DomainName "LOCAL.TEST" -InstallDNS` --> this is the default and minimal version 

# Rename Client computer 

Go to PowerShell and type : 
`Rename-computer -newName Client1`

# Add a static IP address to the client 
1) `Get-NetAdapter` 

2) `New-NetIPAddress -InterfaceIndex 11 -IPAddress 192.168.153.201 -PrefixLength 24 -DefaultGateway 192.168.153.254 `

## add client to domain 

...
