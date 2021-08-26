LXC is linux container software. Docker is based on it. 

* [How to Install Ubuntu on LXC? – An Easy Guide](https://www.linuxfordevices.com/tutorials/ubuntu/install-ubuntu-on-lxc)

https://ubuntu.com/blog/lxd-client-on-windows-and-macos

https://blog.simos.info/how-to-run-a-windows-virtual-machine-on-lxd-on-linux/

### lxc commands
```
 lxc-create -n centos_lxc -t centos
 lxc-start -d -n myContainer
 lxc-ls --fancy
 lxc-attach -n myContainer
 
```

config files location /var/lib/lxc


### LXD monitor tools.

LXD consists of two parts:
* the daemon (the lxd binary)
* the client (the lxc binary)


This edit and push files into the container.  Is it using ftp like mechanisms below?

```
lxc file pull
lxc file edit
lxc file push
lxc file delete


lxc launch mycontainer alias

lxc profile copy
lxc profile set

lxc image import lxd.tar.gz rootfs.squashfs --alias myimagealias
lxc snapshot
```

### sample yaml files for images
distrobuilder/master/doc/samples

```
sudo distrobuilder build-lxd your.yaml
```

### Site with lxc info
* https://techoverflow.net/category/container/lxc/
* https://wiki.gentoo.org/wiki/LXC
* https://wiki.archlinux.org/title/Linux_Containers
* https://wiki.archlinux.org/title/Linux_Containers


### cheatsheat
https://gist.github.com/berndbausch/a6835150c7a26c88048763c0bd739be6
