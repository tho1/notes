


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

e.g. sqllocaldb create “instance name” 11.3  
create version 11.3

Reference:
https://www.red-gate.com/simple-talk/sql/sql-development/edition-sql-server-best-development-work/
https://docs.microsoft.com/en-us/sql/tools/sqllocaldb-utility?view=sql-server-ver15  breakdown of the command configuration.



More SQL tools.

https://www.heidisql.com/  a small SQL tools.

It mentions connecting to TLS 1.2 in sql server requires MS OLE DBSQL driver.
https://www.microsoft.com/en-us/download/confirmation.aspx?id=56730

https://fishcodelib.com/Database.htm database.net tools.   This also contains lots of other .net tools.

http://www.sqltools.net/ another sql tools. This had the look and feel of PL/SQL developer 

http://squirrel-sql.sourceforge.net/index.php?page=programing This is Java based. 
