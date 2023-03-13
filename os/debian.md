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


#### copy and paste in clipboard
```
Ctrl + Shift + V -> paste contents of my main clipboard (from X)
Ctrl + Shift + C -> copy current selection to clipboard
So to restore that functionality here’s the magic thing you need in your .Xresources file in order to achieve it:

! Restore Ctrl+Shift+(c|v)
URxvt.keysym.Shift-Control-V: eval:paste_clipboard
URxvt.keysym.Shift-Control-C: eval:selection_to_clipboard
URxvt.iso14755: false
URxvt.iso14755_52: false
Once you have that just merge settings with:

xrdb -merge .Xresources
```
Reference https://www.tomica.net/blog/2019/01/fixing-urxvt-copy-paste/



#### hardware related commands

##### creating new filesystem.
* https://unix.stackexchange.com/questions/61209/create-and-format-exfat-partition-from-linux

##### mkfs related

* https://learn.microsoft.com/en-us/troubleshoot/windows-server/backup-and-storage/support-for-hard-disks-exceeding-2-tb
* https://man7.org/linux/man-pages/man5/ext4.5.html

```
mkfs.ext3 /dev/sdXX -O sparse_super,large_file -m 0 -T largefile4
mkfs.ext4 /dev/sdXX -O sparse_super,large_file,uninit_bg -E lazy_itable_init=1 -m 0 -T largefile
mkfs.ntfs -f /dev/sdb1

# -m reserved-block-percentage
# -T usage-type
# -E extended-option

```


##### storage monitoring
```
sudo smartctl -c /dev/sda 
sudo smartctl -t long /dev/sda 
sudo smartctl -a /dev/sda 
sudo skdump /dev/sda
```

* https://superuser.com/questions/1037644/samsung-ssd-wear-leveling-count-meaning
* https://help.ubuntu.com/community/Smartmontools

