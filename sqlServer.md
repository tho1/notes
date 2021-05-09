


SQL server 2017 had multiple versions.



main page. 
https://www.microsoft.com/en-ca/sql-server/sql-server-2017

Running on Linux.
https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-editions-and-components-2017?view=sql-server-ver15

Turning on TLS for SQL server.  This provides a bird's eyeview and the terminology used.
https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine?view=sql-server-ver15

https://docs.microsoft.com/en-us/sql/connect/odbc/using-always-encrypted-with-the-odbc-driver?view=sql-server-ver15

Which edition of SQL should you use?  This is a good breakdown.
localDB is the perfect version for testing and local dev. It even lets you decide which version of SQL server to use, and it is small and fast, with less overhead.  
Developer edition mimic the enterprise edition, good for non prod.
And then there are web version, and cloud version for azure.


Problems with the TLS setup.
Got connection error:  SSL Provider. The target principal name is incorrect.
Solution: One needs to enter the fully qualified network name in order to resolve the principal name error.


More information about the service accounts.
SQL server are setup to run on service accounts, and one might been set up to run it on virtual service accounts.

See 
https://sourcedaddy.com/windows-7/managing-service-accounts.html
https://www.itprotoday.com/security/are-you-using-correct-type-windows-service-account
https://community.spiceworks.com/topic/2242023-creating-a-managed-service-account-in-server-2016

Standalone Managed Service Accounts, Group Managed Service Accounts, Virtual Accounts ( starts with Service or NT Service)

See this on troubleshooting.
https://blogs.technet.microsoft.com/askds/2009/09/10/managed-service-accounts-understanding-implementing-best-practices-and-troubleshooting/

Also look at this.
https://developer.ibm.com/answers/questions/343782/why-does-my-odbc-dsn-database-connection-error-wit/



e.g. sqllocaldb create “instance name” 11.3  
create version 11.3

Reference:
https://www.red-gate.com/simple-talk/sql/sql-development/edition-sql-server-best-development-work/
https://docs.microsoft.com/en-us/sql/tools/sqllocaldb-utility?view=sql-server-ver15  breakdown of the command configuration.



More SQL tools.
[a small SQL tool](https://www.heidisql.com)

It mentions connecting to TLS 1.2 in sql server requires MS OLE DBSQL driver.
https://www.microsoft.com/en-us/download/confirmation.aspx?id=56730

https://fishcodelib.com/Database.htm database.net tools.   This also contains lots of other .net tools.

http://www.sqltools.net/ another sql tools. This had the look and feel of PL/SQL developer 

http://squirrel-sql.sourceforge.net/index.php?page=programing This is Java based. 



Commands.

check whether a user had view and execute right for stored-proc.

select name, 
    has_perms_by_name(name, 'OBJECT', 'EXECUTE') as has_execute,
    has_perms_by_name(name, 'OBJECT', 'VIEW DEFINITION') as has_view_definition
from sys.procedures

Reference: https://stackoverflow.com/questions/13152329/finding-stored-procedures-having-execute-permission


Testing ODBC connection
There is 32 bit and 64 bit ODBC administrator. 
What I notice is installing the 64 bit versio will install both 32 and 64 bit drivers.

#### iTesting an OLE connection.
[Installed the OLE version of Microsoft driver](https://www.microsoft.com/en-us/download/details.aspx?id=56730)

It is intalled in C:\windows\SysWow64, and see the attached picture.

In order to test the OLE connection, one can try create an empty file with UDL extension. Click on the file, and it will open a Data Link properties dialog for one to enter the information.



#### Check whether a datbase in a SQL server is still in use.

[Identify SQL Server databases that are no longer in use](https://www.mssqltips.com/sqlservertip/3171/identify-sql-server-databases-that-are-no-longer-in-use)

[How can I tell if a SQL Server database is still being used?](https://dba.stackexchange.com/questions/2050/how-can-i-tell-if-a-sql-server-database-is-still-being-used)


#### Upsize from Access Database to SQL server
[When and How to Upsize Microsoft Access Databases to SQL Server](https://www.fmsinc.com/MicrosoftAccess/SQLServerUpsizing/how/index.htm)

#### Check which service account is the SQL server running in.
[How to find out the account(s) under which the sql server is running?
](https://dba.stackexchange.com/questions/110900/how-to-find-out-the-accounts-under-which-the-sql-server-is-running/110901)
SELECT  DSS.servicename,
        DSS.startup_type_desc,
        DSS.status_desc,
        DSS.last_startup_time,
        DSS.service_account,
        DSS.is_clustered,
        DSS.cluster_nodename,
        DSS.filename,
        DSS.startup_type,
        DSS.status,
        DSS.process_id
FROM    sys.dm_server_services AS DSS;

### Cleaning up the VLF

https://sqlespresso.com/2017/08/23/vlfs-the-forgotten-foe/
