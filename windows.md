This stores the Windows 


Windows god mode to access all command in one place.

https://www.techrepublic.com/article/how-to-use-god-mode-in-windows-10/


* get the windows hardware info. ```wmic computersystem get model,name,manufacturer,systemtype```
* locate system service tag ```wmic bios get serialnumber```
* Windows key ```wmic path softwarelicensingservice get OA3xOriginalProductKey```
* Window key using Linux ```sudo cat /sys/firmware/acpi/tables/MSDM | tail -1```

Reference: https://www.cyberciti.biz/faq/linux-find-windows-10-oem-product-key-command/
