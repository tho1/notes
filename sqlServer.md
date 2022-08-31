


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

#### Check whether a database in a SQL server is still in use.

[Identify SQL Server databases that are no longer in use](https://www.mssqltips.com/sqlservertip/3171/identify-sql-server-databases-that-are-no-longer-in-use)

[How can I tell if a SQL Server database is still being used?](https://dba.stackexchange.com/questions/2050/how-can-i-tell-if-a-sql-server-database-is-still-being-used)

#### Resolve SQL server connections 
    [SQL Server Always On Listeners] (https://www.sqlshack.com/sql-server-always-on-listeners/)
    [TROUBLESHOOTING SQL SERVER LISTENER CONNECTIVITY](https://www.eraofdata.com/sql-server/troubleshooting-sql-server-listener-connectivity/)
    [Resolve Error 40: Could Not Open a Connection to SQL Server](https://www.c-sharpcorner.com/article/resolve-error-40-could-not-open-a-connection-to-sql-server/)
    [Resolving could not open a connection to SQL Server errors](https://www.mssqltips.com/sqlservertip/2340/resolving-could-not-open-a-connection-to-sql-server-errors/)

    [Resolving could not open a connection to SQL Server errors](https://www.mssqltips.com/sqlservertip/2340/resolving-could-not-open-a-connection-to-sql-server-errors/)
    [Different Ways to Connect to SQL Server Using sqlcmd](https://www.mssqltips.com/sqlservertip/5133/different-ways-to-connect-to-sql-server-using-sqlcmd/)


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

### Check the list of tables and columns defined in a database
```
SELECT
  	TABLE_NAME,
    COLUMN_NAME
FROM
  	INFORMATION_SCHEMA.COLUMNS
 ```
 
### check the tables inside a sql server

#### SQL server 2000
```
SELECT
  *
FROM
  SYSOBJECTS
WHERE
  xtype = 'U';
```

#### SQL server 2005 and after
```
SELECT
  *
FROM
  INFORMATION_SCHEMA.TABLES;
```

### check the disk spaces used by a particular table
```sp_spaceused '[HumanResources].[Department]'```

see mssqltips.com/sqlservertip/1177/determining-space-used-for-all-tables-in-a-sql-server-database/

### https://www.mssqltips.com/sqlservertip/1476/how-to-read-log-file-in-sql-server-using-tsql/


### check the list of entries in each table.
```
  select t.name TableName, i.rows Records
from sysobjects t, sysindexes i
where t.xtype = 'U' and i.id = t.id and i.indid in (0,1)
order by TableName;
```

see https://stackoverflow.com/questions/1443704/query-to-list-number-of-records-in-each-table-in-a-database

### This checks the entries used by the system

```
SELECT 
 t.NAME AS TableName,
 i.name AS indexName,
 SUM(p.rows) AS RowCounts,
 SUM(a.total_pages) AS TotalPages, 
 SUM(a.used_pages) AS UsedPages, 
 SUM(a.data_pages) AS DataPages,
 (SUM(a.total_pages) * 8) / 1024 AS TotalSpaceMB, 
 (SUM(a.used_pages) * 8) / 1024 AS UsedSpaceMB, 
 (SUM(a.data_pages) * 8) / 1024 AS DataSpaceMB
FROM 
 sys.tables t
INNER JOIN  
 sys.indexes i ON t.OBJECT_ID = i.object_id
INNER JOIN 
 sys.partitions p ON i.object_id = p.OBJECT_ID AND i.index_id = p.index_id
INNER JOIN 
 sys.allocation_units a ON p.partition_id = a.container_id
WHERE 
 t.NAME NOT LIKE 'dt%' AND
 i.OBJECT_ID > 255 AND  
 i.index_id <= 1
GROUP BY 
 t.NAME, i.object_id, i.index_id, i.name 
ORDER BY 
 OBJECT_NAME(i.object_id) 
```
