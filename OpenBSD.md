### Installing openbsd
https://sohcahtoa.org.uk/openbsd.html
https://news.ycombinator.com/item?id=20344766 some thoughts on using openbsd as a workstation
https://medium.com/linux-gossip/openbsd-6-4-installing-a-seriously-underrated-os-in-a-virtual-machine-f5848ee5a25a

### Make openbsd a desktop system with GUI
https://framagit.org/3hg/isotop/-/blob/master/README.md

### Other BSD variant.
Most are not getting a lot of updates.  Not enough users?

* https://en.wikipedia.org/wiki/PacBSD
* https://www.debian.org/ports/kfreebsd-gnu/
* https://www.reddit.com/r/UbuntuBSD/comments/65dzat/is_ubuntubsd_dead/
* [Some notes why people like FreeBSD, compare to linux.](https://www.over-yonder.net/~fullermd/rants/bsd4linux/01 )


### migrate openbsd userland to Linux
https://github.com/leahneukirchen/outils interesting to study the commands and the tools source code.  the coding style.

### make openbsd smaller
https://unix.stackexchange.com/questions/272881/openbsd-reduce-the-base-install-size-for-smaller-systems


### Conversion between Unix and Dos format

#### DOS to UNIX

```
tr -d '\r' < input.file > output.file
perl -pi -e 's/\r\n/\n/g' input.file
```

#### UNIX to DOS
```
sed 's/$'"/`echo \\\r`/" input.txt > output.txt
```
