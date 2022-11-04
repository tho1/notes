Windows trick.

* get the windows hardware info. ```wmic computersystem get model,name,manufacturer,systemtype```
* locate system service tag ```wmic bios get serialnumber```
* Windows key ```wmic path softwarelicensingservice get OA3xOriginalProductKey```
* Window key using Linux ```sudo cat /sys/firmware/acpi/tables/MSDM | tail -1```
* Windows god mode to access all command in one place. Create a folder with the following strings.  
* Windows 7 & 8: GodMode.{ED7BA470-8E54-465E-825C-99712043E01C} 
* Windows 10: GodMode.{ED7BA470-8E54-465E-825C-99712043E01C}

Check the network setup and 
* netsh 
* ```wlan show profiles SSID``` 
* ```wlan show profiles SSID key=clear```

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


* https://www.w3schools.com/python/numpy/default.asp
* https://www.w3schools.com/python/pandas/default.asp
