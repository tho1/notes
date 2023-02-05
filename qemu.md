## QEMU
* [Runnning ArchLinux in QEMU](https://www.reddit.com/r/archlinux/comments/68jvew/installing_archlinux_in_a_qemu_kvm_vm/)
* [Running FreeBSD in QEMU](https://stackoverflow.com/questions/49656395/how-to-boot-freebsd-image-under-qemu/64027161#64027161)
* [Running openwrt in QEMU](https://openwrt.org/docs/guide-user/virtualization/qemu)

### Shortcut keys
```
ctrl-alt-F toggle screen
ctrl-alt-G toggle between vm and the host
```

## image related
qemu-img  https://dustymabe.com/2015/01/11/qemu-img-backing-files-a-poor-mans-snapshotrollback/
[overlay image] (https://wiki.archlinux.org/title/QEMU#Overlay_storage_images)

### image overlay
```
 qemu-img create -o backing_file=img1.raw,backing_fmt=raw -f qcow2 img1.cow
 qemu-img rebase -u -b /new/img1.raw /new/img1.cow
```

convert image format
```
qemu-img convert -f raw -O qcow2 vm_hdd.img vm_hdd.qcow2
```

### image conversion
```
qemu-img convert -O vdi gnome.qcow2 gnome.vdi
#if its a raw image then:
VBoxManage convertdd opnstk.raw VBox.vdi --format VDI
```
Reference: https://gist.github.com/mamonu/671038b09f5ae9e034e8

### vnc connect
```
-vnc :0
-vnc 192.168.1.5:0
-vnc 0.0.0.0:5
-vnc 0.0.0.0:1 -k en-us
####  Require that password based authentication is used for client connections ####
-vnc 0.0.0.0:1,password -k en-us

qemu-kvm -S -M rhel5.4.0 -m 1024 -smp 1 -vnc 0.0.0.0:1 -k en-us -name centos1 -monitor pty -boot c -drive file=/var/lib/libvirt/images/centos1.img
```
Reference https://www.cyberciti.biz/faq/linux-kvm-vnc-for-guest-machine/


### Questions and Answers.
* https://stackoverflow.com/questions/6710555/how-to-use-qemu-to-run-a-non-gui-os-on-the-terminal
* https://stackoverflow.com/questions/19565116/redirect-qemu-window-output-to-terminal-running-qemu
* https://unix.stackexchange.com/questions/250938/qemu-usb-passthrough-windows-guest
* https://unix.stackexchange.com/questions/131942/qemu-2-0-windows-guest-mouse-stops-working-vnc-when-using-usb-passthrough?rq=1
* https://unix.stackexchange.com/questions/13590/really-light-weight-linux-for-vm-no-extensions
* https://unix.stackexchange.com/questions/156816/emulate-raspberrypi-using-qemu
* https://stackoverflow.com/questions/70351250/is-it-possible-to-copy-files-to-qemu-image-without-running-qemu  copy files using nbd. Useful
* https://www.reddit.com/r/VFIO/comments/i12uyn/virtiofs_is_amazing_plus_how_i_set_it_up/
* https://github.com/virtio-win/kvm-guest-drivers-windows/issues/126
* https://discuss.linuxcontainers.org/t/can-you-use-a-qemu-disk-image-to-boot-an-lxd-vm/8030




## Windows related
### using virtio drivers for Windows VM
* https://leduccc.medium.com/improving-the-performance-of-a-windows-10-guest-on-qemu-a5b3f54d9cf5

### hyper V related
* https://blog.wikichoon.com/2014/07/enabling-hyper-v-enlightenments-with-kvm.html

### LXC related
https://unix.stackexchange.com/questions/50201/how-to-configure-external-ip-addresses-for-lxc-guests

### Comparision to docker
* [Containers in Redhat](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/building_running_and_managing_containers/index) This also provide the scenarios where container put into usage.
* [Container to host](https://sophilabs.com/blog/communication-between-containers-and-host-machine)
* [Communication between container](https://docs.oracle.com/cd/E37670_01/E75728/html/section_rsr_p2z_fp.html)

### Networking on QEMU
* [Between host and guest](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_administration_guide/sect-qemu_guest_agent-set_up_communication_between_guest_agent_and_host)
* [kvm networking](https://www.linux-kvm.org/page/Networking)
* [private network between vm](https://serverfault.com/questions/383208/creating-a-private-network-for-two-vms)
* [kvm on wireless interface](https://unix.stackexchange.com/questions/159191/setup-kvm-on-a-wireless-interface-on-a-laptop-machine) Good post. Lots of instructions
* https://unix.stackexchange.com/questions/124681/how-to-ssh-from-host-to-guest-using-qemu
* https://unix.stackexchange.com/questions/318947/how-to-allow-guest-os-to-access-internet-in-qemu
* https://people.debian.org/~aurel32/qemu/armhf/
* https://stackoverflow.com/questions/74986448/how-to-emulate-qemu-to-connect-server-sockets



## other virtualization methods

### private network for virtualbox
* [virtualbox to emulate a network](https://www.brianlinkletter.com/2016/07/how-to-use-virtualbox-to-emulate-a-network/)


### OS
https://www.ics.uci.edu/~aburtsev/238P/
https://pdos.csail.mit.edu/6.828/2020/schedule.html

### publication
https://pdos.csail.mit.edu/publications/

### xv6
https://pdos.csail.mit.edu/6.828/2020/xv6.html

### compile qmeu and virsh
https://developer.ibm.com/tutorials/compiling-libvirt-and-qemu/


### qemu monitor
https://kashyapc.wordpress.com/tag/qemu/
https://en.wikibooks.org/wiki/QEMU/Monitor#:~:text=The%20monitor%20is%20accessed%20from,back%20to%20the%20guest%20OS.
https://qemu.readthedocs.io/en/latest/system/monitor.html


### virsh
#### provide blockpull and blockcommit.
* blockcommit commits the change to the backing file
* blockpull commits the backing file.
* blockcommit is faster than blockpull

### AutoInstall openbsd.
* https://www.skreutz.com/posts/autoinstall-openbsd-on-qemu/  This is cool!

### General Info
* [QEMU gentoo wiki](https://wiki.gentoo.org/wiki/QEMU/Options#Hard_drive)
* [QEMU arch wiki](https://wiki.archlinux.org/title/QEMU#Creating_a_hard_disk_image)
* [Enable huge pages](https://wiki.archlinux.org/title/KVM#Enabling_huge_pages)

### Books
* [KVM Virtualization Cookbook](https://www.packtpub.com/product/kvm-virtualization-cookbook/9781788294676)
* [Mastering KVM virtualization](https://www.packtpub.com/product/mastering-kvm-virtualization-second-edition/9781838828714)

