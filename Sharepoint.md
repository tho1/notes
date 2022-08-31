Import-Module ServerManager

Add-WindowsFeature Net-Framework-Features,Web-Server,Web-WebServer,Web-Common-Http,Web-Static-Content,Web-Default-Doc,Web-Dir-Browsing,Web-Http-Errors,Web-App-Dev,Web-Asp-Net,Web-Net-Ext,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Health,Web-Http-Logging,Web-Log-Libraries,Web-Request-Monitor,Web-Http-Tracing,Web-Security,Web-Basic-Auth,Web-Windows-Auth,Web-Filtering,Web-Digest-Auth,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Mgmt-Tools,Web-Mgmt-Console,Web-Mgmt-Compat,Web-Metabase,WAS,WAS-Process-Model,WAS-NET-Environment,WAS-Config-APIs,Web-Lgcy-Scripting,Windows-Identity-Foundation,Server-Media-Foundation,Xps-Viewer –Source E:\Source\sxs


Find-PackageProvider -Name "Nuget" -AllVersions

Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.208" -Force

Install-Script -Name AutoSPSourceBuilder

AutoSPSourceBuilder.ps1 -SharePointVersion "2019" -SourceLocation "D:" -Destination "C:\SPInstall\SP2019" -UpdateLocation "C:\SPInstall\SP2019\Patches" -CumulativeUpdate "January 2019" -GetPrerequisites


#Enable Credential Security Support
Enable-WSManCredSSP –Role Server;

#Disable Kerberos and Negotiate Authentication
winrm set winrm/config/service/Auth @{Kerberos="false"};
winrm set winrm/config/service/Auth @{Negotiate="false"}

#Allow Remote Server Management
Configure-SMRemoting.exe -enable

Test-WSMan srv-sp2019WFE

### helpful links on installing Sharepoint 2019
*[Deploying a SharePoint 2019 Development Environment – Install SharePoint 2019 with AutoSPInstaller](https://prairiedeveloper.com/2019/03/install-sharepoint-2019-with-autospinstaller/)
*[Deploying a SharePoint 2019 Development Environment – Preparing Servers for SharePoint 2019](https://prairiedeveloper.com/2019/03/preparing-servers-for-sharepoint-2019/)
*[This setups the xml file to auto install Sharepoint](https://autospinstaller.com/Guide)
