SSH notes

tips:
TURN OFF ChallengeResponseAuthentication and PasswordAuthentication in /etc/ssh/sshd_config

https://security.stackexchange.com/questions/112528/why-is-leaving-a-passworded-ssh-over-the-internet-so-bad

non-standard port
connection rate limiting (1 new connection per minute per IP)
fail2ban

shellinabox

multiple advices.
https://forums.whirlpool.net.au/archive/2745989

https://wiki.dd-wrt.com/wiki/index.php/Knockd

IP rating
https://making.pusher.com/per-ip-rate-limiting-with-iptables/

https://making.pusher.com/per-ip-rate-limiting-with-iptables/ rate limiting

https://www.liberiangeek.net/2014/07/enable-ssh-key-logon-disable-password-password-less-logon-centos/

https://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html


wireguard. 
alternative to openvpn


setting up dropbear server and client
https://linuxconfig.org/how-to-install-and-configure-dropbear-on-linux

dropbear had its own client called dbclient

To generate the private key
$ dropbearkey -t rsa -s 4096 -f key

To genrate the public key
$ dropbearkey -y -f key | grep ^ssh-rsa > key_public

https://developer.ridgerun.com/wiki/index.php?title=Dropbear#How_to_get_Dropbear_public_and_private_keys_in_target_manually

Putty setup
https://devops.ionos.com/tutorials/use-ssh-keys-with-putty-on-windows/

https://superuser.com/questions/8077/how-do-i-set-up-ssh-so-i-dont-have-to-type-my-password



OPENSSL for windows platform.
Go to https://curl.se/windows/ and get the windows binary.


https://stackoverflow.com/questions/19441155/how-to-create-a-self-signed-certificate-for-a-domain-name-for-development?noredirect=1&lq=1   create self signed certificate in IIS



Tomcat related.

https://superuser.com/questions/747377/enable-tls-1-1-and-1-2-for-clients-on-java-7
https://stackoverflow.com/questions/9749339/does-tomcat-support-tls-v1-2

openssl s_client -connect localhost:8443 -tls1_1
openssl s_client -connect localhost:8443 -tls1_2


https://medium.com/the-new-control-plane/generating-self-signed-certificates-on-windows-7812a600c2d8
https://stackoverflow.com/questions/19441155/how-to-create-a-self-signed-certificate-for-a-domain-name-for-development?noredirect=1&lq=1  good example on multiple wildcard domain.

https://stackoverflow.com/questions/7580508/getting-chrome-to-accept-self-signed-localhost-certificate?noredirect=1&lq=1

become your own CA. another good example.
