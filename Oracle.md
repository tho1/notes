Oracle is an enterprise database.

### installation of Oracle client

### Oracle Client for Windows 
It comes with 32 bit and 64 bit versions.  64 bit versions can only be installed in 64 bit Windows. 

Registry setup. 

Oracle writes to Windows registry for 32 bit or 64 bit installation.

Here are some common registry values added to registry.  See 

* [Registry setup](https://docs.oracle.com/en/database/oracle/oracle-database/19/ntqrf/about-hkey-local-machine.html#GUID-33BEB17A-6151-4192-B24B-3EABAE5A2482)
* The registry for Windowss 32 bit and 64 bit are saved in different locations. 
* Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\ORACLE for 32 bit. 
* Computer\HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE for 64 bit version.

### ODBC clients setup
* Oracle also provide a driver for Windows application. see https://docs.oracle.com/database/121/ADFNS/adfns_odbc.htm#ADFNS1118


### sqlplus
* sqlplus username@instance
* To turn on logging in sqlplus
* spool spoolfile.log
* SQL> set echo on
* SQL> set serveroutput on form word_wrapped;

