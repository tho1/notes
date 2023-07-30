Windows trick.

### basic tricks.
* get the windows hardware info. ```wmic computersystem get model,name,manufacturer,systemtype```
* locate system service tag ```wmic bios get serialnumber```
* Windows key ```wmic path softwarelicensingservice get OA3xOriginalProductKey```
* Window key using Linux ```sudo cat /sys/firmware/acpi/tables/MSDM | tail -1```
* Windows god mode to access all command in one place. Create a folder with the following strings.  
* Windows 7 & 8: GodMode.{ED7BA470-8E54-465E-825C-99712043E01C} 
* Windows 10: GodMode.{ED7BA470-8E54-465E-825C-99712043E01C}

### Check the network setup and view past entries. 
* netsh 
* ```wlan show profiles SSID``` 
* ```wlan show profiles SSID key=clear```

### windows image command 
https://www.windowscentral.com/how-use-dism-command-line-utility-repair-windows-10-image

### disable auto update
```reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU" /v NoAutoUpdate /t REG_DWORD /d 1 /f```

### specify start layout for windows 10 pc
```reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer" /v SpecialRoamingOverrideAllowed /t REG_DWORD /d 1 /f```

### check storage health
```
wmic diskdrive get status
```

### backup windows partition as squashfs
```
mount -o ro /dev/sda5 /mnt/windows
mksquashfs /mnt/windows/ ~/windows7.backup.squashfs
```

### extend trial period for windows server
```
slmgr -dlv
slmgr -rearm
```
Reference: https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn502540(v=ws.11)


### redirect time zones
```reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows NT\Terminal Services" /v fEnableTimeZoneRedirection /t REG_DWORD /d 1 /f````

### windows newsgroup achive
* https://microsoft.public.vstudio.general.narkive.com/

### windows server core option
* https://learn.microsoft.com/en-us/windows-server/administration/server-core/what-is-server-core lists the application disabled in a table 

### Using windows laptop as wifi sharing
* https://superuser.com/questions/867394/internet-connection-sharing-with-wireless
* https://4sysops.com/members/michael-pietroforte/
* https://www.versatek.com/blog/why-4g-lte-gateway-is-still-a-win/
* https://www.pcerror-fix.com/how-to-view-or-change-a-hosted-network-settings-in-windows-10

#### laptop as wireless hotspot 
Step 1. Run the follwoing command will lists the properties of the wireless driver.  Look for a line called "Hosted Network support: Yes" 

```
netsh wlan show drivers
```

Step 2. defines a new network
The hosted network mode has been set to allow.
The SSID of the hosted network has been successfully changed.
The user key passphrase of the hosted network has been successfully changed.

```
C:\WINDOWS\system32>netsh wlan set hostednetwork mode=allow ssid=penpen key=123g
```

Step 3. start the new network
```
C:\WINDOWS\system32>netsh wlan start hostednetwork
```


Step 4. Go to Control Panel > Network and Internet > Network Connections
There should be a new virtual network.

Step 5. Now go to the Local Area Connection. Click properties.
IN the Networking tab.  unclick Internet Protocol Version6.
IN the Networking tab.  check IPv4 is enabled.
Click the Sharing tab. on the top.
    deselect Allow other network users to connect through this computer's intern
    There should be a drop down list.  Select the new one you created.
    Local Area Network 11.

Step 6. Now go back to the Local Network Connection recently created. Check the general tab.
check the IPv4 connectivity: Internet

Step 7. Now ping outside.

C:\WINDOWS\system32>netsh wlan stop hostednetwork
The hosted network started.


Reference 
* https://www.cyberciti.biz/faq/linux-find-windows-10-oem-product-key-command/
* https://www.techrepublic.com/videos/how-to-use-god-mode-in-windows-10/


* https://www.microsoft.com/en-US/cloudskillschallenge/ignite/officialrules/2022
* https://learn.microsoft.com/en-us/certifications/azure-administrator/ AZ-104
* 
* https://learn.microsoft.com/en-us/certifications/exams/az-305?wt.mc_id=ignite22_cloudskillschallenge_cschome_cnl AZ-305

* https://learn.microsoft.com/en-us/certifications/devops-engineer/ AZ-400, AZ-104 prereq.
* https://learn.microsoft.com/en-us/certifications/exams/dp-100  DP-100 no prereq.
* https://learn.microsoft.com/en-us/certifications/power-platform-app-maker/ PL-100 no-prereq.
* https://learn.microsoft.com/en-us/certifications/d365-functional-consultant-field-service/ MB-240 no prereq
* https://learn.microsoft.com/en-us/certifications/d365-functional-consultant-field-service/ MS-700
* https://learn.microsoft.com/en-us/certifications/m365-teams-voice-engineer-expert/ MS-720  team associate.
* https://learn.microsoft.com/en-us/certifications/security-operations-analyst/  SC-200 security exam.
* https://learn.microsoft.com/en-ca/training/challenges?id=8c527742-d628-4e50-964c-852e63e5018c accessibility challenges

* https://hackr.io/blog/microsoft-azure-certification-guide
* https://cloudacademy.com/blog/microsoft-azure-certifications-which-is-right-for-you-and-your-team/
* https://learn.microsoft.com/en-us/certifications/practice-assessments-for-microsoft-certifications
* 


*  AZ104, AZ204, AZ305
*  https://acloudguru.com/blog/engineering/which-azure-certification-is-right-for-me
*  AZ-305: Designing Microsoft Azure Infrastructure Solutions
	Aligning Challenge: Microsoft Ignite: Intelligent Cloud Challenge

Candidates for this exam should have advanced experience and knowledge of IT operations, including networking, virtualization, identity, security, business continuity, disaster recovery, data platforms, and governance. A professional in this role should manage how decisions in each area affect an overall solution. In addition, they should have experience in Azure administration, Azure development, and DevOps processes.
Design identity, governance, and monitoring solutions (25-30%)
Design data storage solutions (25-30%)
Design business continuity solutions (10-15%)
Design infrastructure solutions (25-30%)

* AI challenge.
* https://github.com/MicrosoftDocs/ml-basics/blob/master/challenges/01%20-%20Flights%20Challenge.ipynb
* https://github.com/MicrosoftDocs/ml-basics/blob/master/challenges/02%20-%20Real%20Estate%20Regression%20Challenge.ipynb
* 
* https://www.w3schools.com/python/numpy/default.asp
* https://www.w3schools.com/python/pandas/default.asp


## wifi modem specific

* https://communityforums.rogers.com/t5/Internet/How-to-change-UDP-timeout-on-Rogers-CODA-4582U/td-p/495500
* https://communityforums.rogers.com/t5/Internet/CODA-4582U-in-bridge-mode-can-t-access-at-192-168-100-1/td-p/448031/page/2
* https://forums.redflagdeals.com/how-add-router-hitron-coda-4582-2228005/

* 


# com programmer's cookbook
https://learn.microsoft.com/en-us/previous-versions/ms809982(v=msdn.10)

