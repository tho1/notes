Was trying to grant more heap space to the Websphere application server.  Assign 2GB of RAM to it. and the admin console refuses to start.

To set the heap size, one goes Application Server --> Server -->  JVM Argument --> Java and Process Defintion --> Java Virtual Machine.  
And one an set the maximum heap size.  

After setting it to 2048MB for the heap size.  The Websphere Application server refuse to start, admin console refuses to start 

Ended up need to modify the server.xml manually.  Caveat: Make a copy of the server.xml before modification.

One can find the server.xml in the usual location.  
C:\Program Files\IBM\WebSphere\AppServer\profiles\AppSrv01\config\cells\YourHostNameNode01Cell\nodes\YourHostNameNode01\servers\server1\server.xml 

Look for the fields initialHeapSize and maximumHeapSize for the value to change.

<jvmEntries xmi:id="JavaVirtualMachine_11831221343434" verboseModeClass="false" verboseModeGarbageCollection="false" 
verboseModeJNI="false" initialHeapSize="1024" maximumHeapSize="1024" runHProf="false" hprofArguments="" debugMode="false" 
debugArgs="-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=7777" 
genericJvmArguments="-Xquickstart" executableJarFileName="" disableJIT="false">

Change the value, and restart the application server.

More information can be found in https://www.ibm.com/support/pages/how-increase-jvm-heap-size-was-serverxml
