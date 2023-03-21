### Maven is a build tool targetted for Java based ecosystems.

### Issues when accessing the code behind the firewall.

```
mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```

pass ```-Djavax.net.ssl.trustStoreType=WINDOWS-ROOT``` maven_options
use for http repository  http://insecure.repo1.maven.org/maven2/

```
 <repositories>
        <repository>
            <id>central</id>
            <name>Maven Plugin Repository</name>
            <url>http://repo1.maven.org/maven2</url>
            <layout>default</layout>
            <snapshots>
                <enabled>false</enabled>
            </snapshots>
            <releases>
                <updatePolicy>never</updatePolicy>
            </releases>
        </repositor
```


save the maven repo certificate as mavenCert.cer
``` 
keytool -import -file C:\temp\mavenCert.cer -keystore C:\temp\mavenKeystore

mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false -Djavax.net.ssl.trustStore=C:\temp\mavenKeystore
```
Set the truststore value in MAVEN_OPTS



* https://maven.apache.org/guides/mini/guide-repository-ssl.html
* https://stackoverflow.com/questions/49176390/set-jre-to-use-windows-trust-store-specifically-the-users-trust-store
* https://stackoverflow.com/questions/25911623/problems-using-maven-and-ssl-behind-proxy

### gradle points to use Windows-ROOT as the certificate
```
systemProp.javax.net.ssl.trustStore=NUL
systemProp.javax.net.ssl.trustStoreType=Windows-ROOT
```


### mvn command lines.

clear the build.
```
mvn clean install -DskipTests -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true -Dmaven.wagon.http.ssl.ignore.validity.dates=true
```



mvn clean install -DskipTests -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true -Dmaven.wagon.http.ssl.ignore.validity.dates=true

mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false


mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false -DskipTests -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.all


ll=true -Dmaven.wagon.http.ssl.ignore.validity.dates=true


 # Java 8
 keytool -import -trustcacerts -alias <named-file> -file <certificate-file-path> -keystore "$JAVA_HOME/jre/lib/security/cacerts"

 # Java 11
 keytool -import -trustcacerts -alias <named-file> -file <certificate-file-path> -keystore "$JAVA_HOME/lib/security/cacerts"


https://stackoverflow.com/questions/25911623/problems-using-maven-and-ssl-behind-proxy?answertab=trending#tab-top
Now open a command prompt and type (use your own paths):

keytool -import -file C:\temp\mavenCert.cer -keystore C:\temp\mavenKeystore

Now you can run the command again with the parameter

-Djavax.net.ssl.trustStore=C:\temp\mavenKeystore

Under linux use absolute path

-Djavax.net.ssl.trustStore=/tmp/mavenKeystore

otherwise this will happen

Like this:

mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false -Djavax.net.ssl.trustStore=C:\temp\mavenKeystore

mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false


use https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-deploy-plugin/2.7/maven-deploy-plugin-2.7.pom

cert is repo1.maven.org

should use https://repo.maven.apache.org/maven2


-- maven setup.


<proxies>
 
 <!-- Proxy for HTTP -->
 
 <proxy>
 
  <id>optional</id>
 
  <active>true</active>
 
  <protocol>http</protocol>
 
 <username>x</username>
 
  <password>yourpassword</password>
 
  <host>proxy</host>
 
  <port>8080</port>
 
  <nonProxyHosts>local.net</nonProxyHosts>
 
 </proxy>
 
 
 
 
 
 
</proxies>


 <profiles>
   
   <profile>
     <id>myprofile</id>
     <repositories>
      <repository>
            <id>central</id>
            <name>Maven Plugin Repository</name>
            <url>http://insecure.repo1.maven.org/maven2/</url>
            <layout>default</layout>
            <snapshots>
                <enabled>false</enabled>
            </snapshots>
            <releases>
                <updatePolicy>never</updatePolicy>
            </releases>
        </repository>
     </repositories>
   </profile>  
   </profiles>
 
 <activeProfiles>
   <activeProfile>myprofile</activeProfile>
 </activeProfiles>
