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
