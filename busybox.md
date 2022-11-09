# BusyBox
busybox topics

```
# create the symlinks for the busybox tools
./busybox --list|./busybox xargs -n1 ./busybox ln -s busybox
```

# Reference
1. [BUSYBOX ON THE FREEBSD](https://smallhacks.wordpress.com/2019/07/08/busybox-on-the-freebsd/)
 

# move files to newdir less than 1 day old
find . -maxdepth 1 -type f -exec mv {} /newdir \;
