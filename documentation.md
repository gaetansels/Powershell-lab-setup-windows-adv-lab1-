
##Server Core Setup

### Context
I have installed Windows Server 2025 as Server Core on a new VM. This server will be promoted to a Domain Controller for the LOCAL.TEST forest.

Below my lab setup : 

![something](images/winadv_lab1_p1.png)

**TASKS:**
- Change Hostname
- Change IP address (IP/SM/DG/DNS)
- update the server after installation --> best practice
- Install New role -> AD-Domain-Services
- Upgrade server_core to DC in the new forest

##Change Hostname 

'get-help rename-computer -examples'  
