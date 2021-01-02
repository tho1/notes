IIS server notes.

Mainly used for setting up the IIS 10 in Windows 10 and Windows server 2016

URL-Write
Tried to look for the feature in Window feature, but end up need to download the extension separately from Microsoft

Step 1
[url-rewrite download](https://www.iis.net/downloads/microsoft/url-rewrite)

Step 2 see
1. [IIS Redirect HTTP to HTTPS](https://www.namecheap.com/support/knowledgebase/article.aspx/9953/38/iis-redirect-http-to-https/) 
2. [mod rewrite](https://hostadvice.com/how-to/how-to-enable-mod_rewrite-on-iis/)
3. [URL rewrite](https://www.cyotek.com/blog/installing-the-url-rewrite-module-into-internet-information-services)



Plain jane static website locally.
1. [build static website] https://docs.microsoft.com/en-us/iis/manage/creating-websites/scenario-build-a-static-website-on-iis
2. Go to Authentication tab disable ASP.NET Impersonation.
3. Enable Directory browsing to able to see the directory.


Setting up the IIS passthrough.

This setup worked for me.

1. Windows 10 64 bit.
2. IIS 10.0 
3. Tomcat 9.0.26 32 bit 
4. JDK 1.8.0.221 32 bit
5. isapi_redirect.dll 32 bit with the extension i386 for 32 bit

1. Install Oracle JDK
2. Install Tomcat in C:\bin\apache-tomcat-9.0.41
3. Create a setclasspath.bat using the zip version.
4. Make sure tomcat able to startup 
5. Create a directory in Tomcat e.g. C:\bin\apache-tomcat-9.0.41\isapi
6. Copy the isapi_redirect.dll in C:\bin\apache-tomcat-9.0.41\isapi
7. Create a file isapi_redirect.properties
8. Create worker.properties and uriworkermap.properties and save in C:\bin\apache-tomcat-9.0.41\conf
9. Go to IIS at the hostname level, and go to ISAPI and CGI restrictions. Click Add, and the isapi_redirect.dll and give it a name like tomcat isapi and click the checkbox "allow extension path to execute"
10. Go to website level, click ISAPI filters add "ISAPI-dll" and the executable of the isapi_redirect.dll
11. right click the website, and add "virtual directory".  Name: jakarta, and the path C:\bin\apache-tomcat-9.0.41\isapi
12. Click on the handler mapping at "virtual directory" level, and click "edit feature permission" on right hand side. Enable "execute" bit.
13. Look for ISAPI-dll, if not there, click Add Script Map. Request Path: *.jsp Executable: C:\bin\apache-tomcat-9.0.41\isapi\isapi_redirect.dll, and Name: JSP.
14. Add Script Map. Request Path: *.dll Executable: C:\bin\apache-tomcat-9.0.41\isapi\isapi_redirect.dll, and Name: ISAPI-dll.
14. Go to application pool of your website. Enable 32-bit applications to true, and set .NET CLR version to v2.0
15. IIS might complain it cannot access the dll file. Go to the directory C:\bin\apache-tomcat-9.0.41\isapi, and right click properties, security tab. grant full control to Authenticated Users, IUSR, DefaultAppPool
16. Go to servers.xml of tomcat and update the AJP connector with the following entry.  port had the match the value in worker.properties, and the  secretRequired="false" for this tomcat version
17. restart tomcat and IIS.
18. go to C:\bin\apache-tomcat-9.0.41\logs\isapi_redirect.log to debug for issue. 

    
    
snippet of server.xml
```
<Connector protocol="AJP/1.3" port="9009"
           redirectPort="8443" secretRequired="false" />
```


setclasspath.bat
```
#Java 1.8
set JAVA_HOME=C:\bin\Java\jdk1.8.0_221
exit /b 0
```

isapi_redirect.properties
```
# needs to use 32 bit isapi_redirect.dll as tomcat is 32 bit, and JDK is 32 bit.
extension_uri=/jakarta/isapi_redirect.dll

# Full path to the log file for the ISAPI Redirector
log_file=C:\bin\apache-tomcat-9.0.41\logs\isapi_redirect.log

# Log level (debug, info, warn, error or trace)
log_level=debug

# Full path to the workers.properties file
worker_file=C:\bin\apache-tomcat-9.0.41\conf\workers.properties

# Full path to the uriworkermap.properties file
worker_mount_file=C:\bin\apache-tomcat-9.0.41\conf\uriworkermap.properties
```

worker.properties
```
worker.list=tomcat01
worker.tomcat01.type=ajp13
worker.tomcat01.host=127.0.0.1
worker.tomcat01.port=9009
```

uriworkermap.properties
```
/*=tomcat01
/examples/*=tomcat01
/admin/*=tomcat01
/manager/*=tomcat01
/host-manager/*=tomcat01
```

web.config in C:\bin\apache-tomcat-9.0.41\isapi
```
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <handlers accessPolicy="Read, Execute, Script">
            <add name="JSP" path="*.jsp" verb="*" modules="IsapiModule" scriptProcessor="C:\bin\apache-tomcat-9.0.41\isapi\isapi_redirect.dll" resourceType="File" preCondition="bitness32" />
            <add name="ISAPI-dll" path="*.dll" verb="*" modules="IsapiModule" scriptProcessor="C:\bin\apache-tomcat-9.0.41\isapi\isapi_redirect.dll" resourceType="File" preCondition="bitness32" />
        </handlers>
    </system.webServer>
</configuration>
```
