This file contains tips and lessons running Fatdog64.

* [Running QEMU to test different fatdog version](http://www.murga-linux.com/puppy/viewtopic.php?t=93598&start=30)
* [Fatdog contributed SFS](http://murga-linux.com/puppy/viewtopic.php?p=794748#794748)  
* [Fatdog ISO builder](http://murga-linux.com/puppy/viewtopic.php?t=105329)          

* [LinuxFest Northwest 2016: Why Puppylinux is awesome and why you should use it](https://www.youtube.com/watch?v=jebMZpEmQlQ)  NorthWest video that talks about the sfs and frugal install

Accessing the NTFS aka Windows partition with read write access.
This turns off the hiberante during shutdown and reboot, in order for the Linux to have write access to the Windows system.  Or else Windows system is read only.

```
powercfg /h off 
```
