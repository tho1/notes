SSH notes

tips:
TURN OFF ChallengeResponseAuthentication and PasswordAuthentication in /etc/ssh/sshd_config
https://security.stackexchange.com/questions/112528/why-is-leaving-a-passworded-ssh-over-the-internet-so-bad

non-standard port
connection rate limiting (1 new connection per minute per IP)
fail2ban

### common commands
https://www.sslshopper.com/article-most-common-openssl-commands.html

### shellinabox

multiple advices.
https://forums.whirlpool.net.au/archive/2745989

https://wiki.dd-wrt.com/wiki/index.php/Knockd

### IP rating
https://making.pusher.com/per-ip-rate-limiting-with-iptables/

https://making.pusher.com/per-ip-rate-limiting-with-iptables/ rate limiting

https://www.liberiangeek.net/2014/07/enable-ssh-key-logon-disable-password-password-less-logon-centos/

https://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html


### wireguard 
alternative to openvpn

setting up dropbear server and client
https://linuxconfig.org/how-to-install-and-configure-dropbear-on-linux

dropbear had its own client called dbclient

To generate the private host key
```
$ dropbearkey -t rsa -s 4096 -f key
```
To create your own key
```
dropbearkey -y -f id_rsa | grep "^ssh-rsa " >> authorized_keys
```

To convert the key for openssh
```
dropbearconvert dropbear openssh id_rsa id_rsa_openssh
```

```
dbclient -i id_rsa 0.0.0.0
ssh -i id_rsa_openssh 0.0.0.0.
```
Reference
https://bugs.freebsd.org/bugzilla/show_bug.cgi?id=220463



## Putty related

https://developer.ridgerun.com/wiki/index.php?title=Dropbear#How_to_get_Dropbear_public_and_private_keys_in_target_manually
Putty setup
https://devops.ionos.com/tutorials/use-ssh-keys-with-putty-on-windows/
https://superuser.com/questions/8077/how-do-i-set-up-ssh-so-i-dont-have-to-type-my-password
https://kb.iu.edu/d/aews


### Windows binary

OPENSSL for windows platform.
Go to https://curl.se/windows/ and get the windows binary. look for openssl binary. Make sur to match the 32 or 64 bit with your OS. 64 bit can use 32 bit binary


### IIS related

https://stackoverflow.com/questions/19441155/how-to-create-a-self-signed-certificate-for-a-domain-name-for-development?noredirect=1&lq=1   create self signed certificate in IIS

### Tomcat related.

https://superuser.com/questions/747377/enable-tls-1-1-and-1-2-for-clients-on-java-7
https://stackoverflow.com/questions/9749339/does-tomcat-support-tls-v1-2

```
openssl s_client -connect localhost:8443 -tls1_1
openssl s_client -connect localhost:8443 -tls1_2
```

https://medium.com/the-new-control-plane/generating-self-signed-certificates-on-windows-7812a600c2d8
https://stackoverflow.com/questions/19441155/how-to-create-a-self-signed-certificate-for-a-domain-name-for-development?noredirect=1&lq=1  good example on multiple wildcard domain.

https://stackoverflow.com/questions/7580508/getting-chrome-to-accept-self-signed-localhost-certificate?noredirect=1&lq=1

become your own CA. another good example.

### httpd related

1. [authentication failed](https://serverfault.com/questions/578336/authentication-failed-user-not-found-in-active-directory)
2. [Authentication failed user not found in active directory])https://serverfault.com/questions/431290/svn-authentication-with-ldap-and-active-directory)

Extract the certificate from the site
```
openssl s_client -connect your.ldap.host:636 2>&1 | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p'
```

Reference:https://stackoverflow.com/questions/7885785/using-openssl-to-get-the-certificate-from-a-server

How to check the connection of a site.

The following use openssl to thes stackoverflow.com SSL features.
```
openssl s_client -connect stackoverflow.com:443
```

The following use the SSLPoke Java Class to check the SSL connection is okay.
```
java -Djavax.net.debug=ssl SSLPoke yourADserver 636
```

### certificates in Windows
* https://superuser.com/questions/1181163/unable-to-use-client-certificates-in-chrome-or-ie-on-windows-10
* https://www.parkytowers.me.uk/thin/Linux/TinycoreSSL.shtml


### Add certificate in Windows
Self signed certificate might run into the problem saying 

In IE
```
Your PC doesn’t trust this website’s security certificate. 
Error Code: DLG_FLAGS_INVALID_CA
```

In Chrome
```
NET::ERR_CERT_AUTHORITY_INVALID
```

Microsoft Edge.  Same error as IE.  They are built by the same company. :-)
```
Error Code: DLG_FLAGS_INVALID_CA
```

Firefox
``` 
Error code: MOZILLA_PKIX_ERROR_SELF_SIGNED_CERT
```

Most people would click on install certificate by clicking on the install certificate button.  Could be the user don't hav enought right to add the certificate.

1. Login in as administrator, and cmd as adminstrator
2. start mmc
3. click add Snap in, certificates, and select whole machine.
4. Right click, All Tasks, import and add the certificate to trusted certificate store


### SVN Authentication with LDAP and Active Directory
https://serverfault.com/questions/431290/svn-authentication-with-ldap-and-active-directory

### Tomcat related.
https://stackoverflow.com/questions/21833732/configure-truststore-in-tomcat
https://stackoverflow.com/questions/7885785/using-openssl-to-get-the-certificate-from-a-server

###  SSL certification generation
openssl req -utf8 -new -key [key file name] -x509 -days [cert lifespan] -out [cert file name] -set_serial [num]

#### options used.
```
req - Certificate Signing Request ( CSR ) Management. 
utf8 - UTF8 unicode
new  - generate new values.
key - key filename
x509 - X.509 Certificate Data Management
days - certificate days
out - name of generated cert file
set_serial - set certificate serial number
```

see [SSL man pages](https://linux.die.net/man/1/openssl)

### Exchange server
1. [Exchange Server TLS guidance Part 3: Turning Off TLS 1.0/1.1](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
2. [Exchange Server TLS guidance, part 1: Getting Ready for TLS 1.2](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
