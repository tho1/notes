Windows trick.



* get the windows hardware info. ```wmic computersystem get model,name,manufacturer,systemtype```
* locate system service tag ```wmic bios get serialnumber```
* Windows key ```wmic path softwarelicensingservice get OA3xOriginalProductKey```
* Window key using Linux ```sudo cat /sys/firmware/acpi/tables/MSDM | tail -1```
* Windows god mode to access all command in one place. Create a folder with the following strings.  
* Windows 7 & 8: GodMode.{ED7BA470-8E54-465E-825C-99712043E01C} 
* Windows 10: GodMode.{ED7BA470-8E54-465E-825C-99712043E01C}

Reference 
* https://www.cyberciti.biz/faq/linux-find-windows-10-oem-product-key-command/
* https://www.techrepublic.com/videos/how-to-use-god-mode-in-windows-10/
