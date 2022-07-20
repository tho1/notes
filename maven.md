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
        </repository>
    </repositories>
```


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
