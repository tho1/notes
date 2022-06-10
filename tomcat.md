Tomcat topics.

### Encryption and proxy
* [How To Encrypt Tomcat 8 Connections with Apache or Nginx on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-encrypt-tomcat-8-connections-with-apache-or-nginx-on-ubuntu-16-04)
* [Tomcat behind Nginx: how to proxy both HTTP and HTTPS, possibly on non-standard ports?](https://stackoverflow.com/questions/30603263/tomcat-behind-nginx-how-to-proxy-both-http-and-https-possibly-on-non-standard)


### Struts 
* [Apache Struts](https://www.jrebel.com/blog/apache-struts)  Provide high level history of Apache struts


### How to add SSL certificate to a JVM
* https://connect2id.com/blog/importing-ca-root-cert-into-jvm-trust-store
* ```java -Djavax.net.debug=ssl SSLPoke yourADserver 636``` This is used to test the SSL connection is all right as expected.


### setting up the tomcat authentication

* Using Varnish and mod_security as a web frontend is a solution
* jaspic-providers.xml needs to be updated using oauth file.

The digest authentication needs to update the following files.  
digest.sh in the /bin folder can be used to create the values. 
 
* /config/server.xml
* /conf/tomcat-users.xml 


#### Update the server.xml with the following realm
<realm className="org.apache.catalina.realm.LockOutRealm>
<realm className="org.apache.catalina.realm.UserDatabaseRealm" resourcename="UserDatabase"> 
	<credentialHandler className="org.apache.catalina.realm.MessageDigestCredentialHandler" 
algorithm="sha-512"/>  
</Realm>
                   
####  Use the digest.sh to create the digest value.
digest.sh -a sha-512 -h
org.apache.catalina.realm.MessageDigestCredentialHandler somepassword   
                   

<Valve className="org.apache.catalina.valves.RemoteAddrValve"
   allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1|.*" />

And in tomcat-users.xml replace the pass 
                                                    
curl -u admin:somepassword host-manager/text/list
lesson: use normal password to login instead for digest password.
realm-howto.html -- add LDAP for realms using LDAP.
                                                   
####
how to perform this in .net
rewrite Tomcat in Go and learn about it.

load balancer.
                                                   
