This file contains tips and lessons running Fatdog64.

* [Running QEMU to test different fatdog version](http://www.murga-linux.com/puppy/viewtopic.php?t=93598&start=30)
* [Fatdog contributed SFS](http://murga-linux.com/puppy/viewtopic.php?p=794748#794748)  
* [Fatdog ISO builder](http://murga-linux.com/puppy/viewtopic.php?t=105329)          

* [LinuxFest Northwest 2016: Why Puppylinux is awesome and why you should use it](https://www.youtube.com/watch?v=jebMZpEmQlQ)  NorthWest video that talks about the sfs and frugal install

#### executable format
* https://unix.stackexchange.com/questions/23535/understanding-linux-executable-formats-and-software-distribution-packages?rq=1

#### compiling
* [Configure,autoconf,etc](https://thoughtbot.com/blog/the-magic-behind-configure-make-make-install)


#### compiling 32 bit
* pass the flag -m32 to gcc
* https://stackoverflow.com/questions/2726993/how-to-specify-preference-of-library-path

example:
```
export CFLAGS='-m32'
export CXXFLAGS='-m32'
export LDFLAGS='-m32'
make
```

#### 64 bit compiling.
```
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --libdir=/usr/lib64 --enable-gui
```

#### multilib 
Fatdog64 supports multilib.  
* [Running 32 bit OS in Fatdog](https://lightofdawn.org/wiki/wiki.cgi/RunSlackoInFatdog)
* https://wiki.gentoo.org/wiki/Multilib
* https://unix.stackexchange.com/questions/425422/how-to-run-old-32-bit-linux-software-in-a-container-inside-a-modern-64-bit-distr
* [How 64bit + 32bit Linux works?](https://oldforum.puppylinux.com/viewtopic.php?t=102072)

#### virtualization.
There is the usermode linux, lxc,  and also qemu. See
* 
* [rw-sandbox.sh](http://www.lightofdawn.org/blog/?viewDetailed=00022)
* see https://oldforum.puppylinux.com/viewtopic.php?p=903665#903665
* lxc-create -t download -n ubuntu1604 -- --dist ubuntu --release xenial --arch amd64

To login you'll have to change the root password of the ubuntu container with:

```
chroot /var/lib/lxc/ubuntu1604/rootfs/
passwd
exit
```

Then you can start it and login with:
lxc-start -n ubuntu1604


#### To mount the NTFS with write access.
Accessing the NTFS aka Windows partition with read write access.
This turns off the hiberante during shutdown and reboot, in order for the Linux to have write access to the Windows system.  Or else Windows system is read only.

```
powercfg /h off 
```

#### viewing the document directory
The /usr/share/doc directory contains lot of information for the software installed.  A lot of the files are in html foramt. Therefore, hosting the directories in web server make lot of sense.

Fatdog64 comes with civet web server. See /etc/init.d/60-civetweb to enable it
Modify the file civetweb.conf to host the directories

open up the /etc/civetweb.conf, and look for the line document_root, change it to document_root /usr/share/doc

```
document_root /usr/share/doc
```

```
/etc/init.d/civetweb start
```

#### viewing non english website in links
download the links source code

```
configure --enable-graphics --enable-utf8
make
make install
```

Now start 'links -g' as graphics mode.  Go to Setup, Fonts, Regular Fonts, and select the other fonts.  In my case, I use WenQuanYi Micro Hei to view website in Chinese

#### overlay and aufs related.
* [aufs vs overlay](https://forum.puppylinux.com/viewtopic.php?t=1910&start=10)
* [HowTo use sfs and changes folder with a full Linux install](https://oldforum.puppylinux.com/viewtopic.php?t=115915)


#### list the steps of the configurations.
