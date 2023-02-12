### debian cheat sheet

####
```
sudo dpkg -i /path/to/deb/file

sudo apt update && sudo apt-get install /path/to/deb/file
apt install /path/to/deb/file

sudo apt-get install install alien  --rpm support
```
####

#### docker for antiX
```
which docker
sudo apt remove docker docker-engine
sudo apt install apt-transport-https ca-certificates software-properties-common curl apt-transport-https
sudo apt install docker-ce

sudo docker run hello-world
```


#### hardware related commands
```
sudo smartctl -c /dev/sda 
sudo smartctl -t long /dev/sda 
sudo smartctl -a /dev/sda 
sudo skdump /dev/sda
```

* https://superuser.com/questions/1037644/samsung-ssd-wear-leveling-count-meaning
* https://help.ubuntu.com/community/Smartmontools

