LDAP notes.


1. [LDAPwiki](ldapwiki.com)
2. ldp ldap connection tool that comes with window
3. AD Explorer, part of sysinternals
4. [Check AD is up](https://docs.microsoft.com/en-us/troubleshoot/windows-server/identity/enable-ldap-over-ssl-3rd-certification-authority)
5. [LDAP Bind errors listing](https://ldapwiki.com/wiki/Common%20Active%20Directory%20Bind%20Errors)

### general stuff

1. [Find name of Active Directory domain controller](https://serverfault.com/questions/78089/find-name-of-active-directory-domain-controller?rq=1)
2. [How to authenticate Linux accounts against an Active Directory and mount a Windows share on login?](https://serverfault.com/questions/135396/how-to-authenticate-linux-accounts-against-an-active-directory-and-mount-a-windo?noredirect=1&lq=1)
3. [How can I find out what AD groups I'm a member of?](https://serverfault.com/questions/111650/how-can-i-find-out-what-ad-groups-im-a-member-of?rq=1)


### apache httpd related

1. [An apache error with LDAP Server on Windows Server 2008 R2](https://serverfault.com/questions/773174/an-apache-error-with-ldap-server-on-windows-server-2008-r2)
2. [LDAP Authentication on Apache denies valid credentials](https://serverfault.com/questions/709919/ldap-authentication-on-apache-denies-valid-credentials)  This provides SSL example too.
3. Password mismatch. Check whether you need the LDAP bind to get it to work.
4. [SVN Authentication with LDAP and Active Directory](https://serverfault.com/questions/431290/svn-authentication-with-ldap-and-active-directory)
5. [Authentication failed user not found in active directory](https://serverfault.com/questions/578336/authentication-failed-user-not-found-in-active-directory)
6. [SVN Edge not authenticating correctly with domain controller](https://serverfault.com/questions/735347/svn-edge-not-authenticating-correctly-with-domain-controller)


### AD related
* [binding with getobject and adsgetobject](https://docs.microsoft.com/en-us/windows/win32/adsi/binding-with-getobject-and-adsgetobject)
* [ne iads ads_authentication_enum](https://docs.microsoft.com/en-us/windows/win32/api/iads/ne-iads-ads_authentication_enum)

* [Recipe 14.2 Encrypting LDAP Traffic with SSL, TLS, or Signing](http://etutorials.org/Server+Administration/Active+Directory.+Windows+server+2003+Windows+2000/Chapter+14.+Security+and+Authentication/Recipe+14.2+Encrypting+LDAP+Traffic+with+SSL+TLS+or+Signing/)

* [Install DSQuery software for Windows Server 2016](http://portal.sivarajan.com/2016/10/windows-server-2016active-directorypart1.html)
* [DSQuery Example](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc725702(v=ws.11))
* [Windows 7 dsquery](https://stackoverflow.com/questions/8514599/windows-7-powershell-cannot-find-dsquery-and-dsget)
* [LDAP Search with PowerShell – Find-LdapObject](https://activedirectoryfaq.com/2015/02/ldap-search-powershell-find-ldapobject/) useful search examples
* [LDAP search with good examples](https://theitbros.com/ldapsearch/)
* [Querying Windows Active Directory server using ldapsearch from command line](https://stackoverflow.com/questions/22224465/querying-windows-active-directory-server-using-ldapsearch-from-command-line)
* [Search Active Directory with Ldapsearch](https://tylersguides.com/guides/search-active-directory-ldapsearch/#:~:text=It%20is%20fairly%20common%20to,search%20Active%20Directory%20with%20ldapsearch.)
* [How To Search LDAP using ldapsearch (With Examples)](https://devconnected.com/how-to-search-ldap-using-ldapsearch-examples/)
* [Powershell example](http://www.jaapbrasser.com/wp-content/uploads/2012/11/Adsisearcher-Examples.txt)

LDAP URLS
* [LDAP URLS](https://ldap.com/ldap-urls/)  General LDAP info.

* [How can i format an LDAP Filter that includes special characters? ('Classic' ASP)](https://stackoverflow.com/questions/20094875/how-can-i-format-an-ldap-filter-that-includes-special-characters-classic-asp)

* [OpenDSObject("LDAP://domain",u,p,...) and get employeeID attribute
](https://www.tek-tips.com/viewthread.cfm?qid=1512832)

* [alternate credentials ](http://www.rlmueller.net/ADOAltCredentials.htm) good example to loop through the code using vbcript

* [Handling ADODB connections in classic ASP
](https://stackoverflow.com/questions/3770017/handling-adodb-connections-in-classic-asp)


### VB.NET connect
https://www.codeproject.com/Articles/8488/Accessing-LDAP-User-list-using-VB-NET
https://www.codeproject.com/Questions/439810/authenticate-user-in-LDAP
https://www.codeproject.com/Questions/526055/LDAPplususerplusAuthenticationplususingplusDirecto
https://www.codeproject.com/Articles/5011/Apply-Single-Sign-On-to-your-application
https://stackoverflow.com/questions/34600846/ldap-vb-net-simple-query

### C# connect
* [LDAP Search utility](https://www.codeproject.com/Articles/1212134/LDAP-Search-Utility)
* [query ldap using ](https://stackoverflow.com/questions/6452531/querying-an-ldap)]
* [manage objects](https://docs.microsoft.com/en-us/troubleshoot/windows-server/identity/directory-service-manage-objects)

### commandline using dsquery
* [list users](https://serverfault.com/questions/49405/command-line-to-list-users-in-a-windows-active-directory-group)
* [search using dsquery](https://serverfault.com/questions/27223/command-line-active-directory-query-email-address-for-username)


### LDAP connection via Java.
* [LDAP: error code 49 - 80090308: LdapErr: DSID-0C0903A9, comment: AcceptSecurityContext error, data 52e, v1db1](https://stackoverflow.com/questions/31411665/ldap-error-code-49-80090308-ldaperr-dsid-0c0903a9-comment-acceptsecurityc)  The issue I ran into is there is binding error.  Check the LDAP URL for possible issues.

### Turn on LDAP debugging in Windows to trace the issue.  This is for Windows only.
* [https://docs.microsoft.com/en-us/troubleshoot/windows-server/identity/turn-on-debug-logging-ldap-client](https://docs.microsoft.com/en-us/troubleshoot/windows-server/identity/turn-on-debug-logging-ldap-client)
