
### sandbox containers
*   https://forum.puppylinux.com/viewtopic.php?t=4966&start=30 LXC container
*   see sandbox-lxc.sh

### boot parameters
pfix=nocopy 
```
menuentry "fossapup64 9.5 - Don't copy SFS files to RAM" {
linux /vmlinuz pfix=nocopy,fsck pmedia=usbflash
initrd /initrd.gz
```
### packages.
* /var/slapt-get
* skopkg since Fatdog 900
* https://www.slackbuilds.org/

### menu itmes.  
* see /etc/xdg
* figure how to modify to restart X with different bpp values??

### keeping savesfs files small
* ```ncdu /aufs/pup_save``` to check the usage.
* recommendations below:
* web browsers cache stored externally.
* Browser profiles (it would probably make sense to symlink the cache folders also)
* certain user-installed /root config folders
* user-installed /usr/share/themes gtk theme folders
* /usr/local/lib/X11/themes user-installed icon folders
* /root/my-applications/bin shell scripts that I'm likely to edit often
* use symlink to keep the files outside of the pupsave, and you can share the settings outside and make it portable.
* https://forum.puppylinux.com/viewtopic.php?t=6257
* https://forum.puppylinux.com/viewtopic.php?t=6257

#### see /usr/bin/google-chrome-spot
* reset the --user-data-dir. pay attention to the location.
```
exec /usr/bin/run-as-spot /opt/google/chrome/google-chrome --user-data-dir="$SPOT_HOME/.config/chrome" "$@"
```
