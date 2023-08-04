### Check the service on startup.
* run command ```ps ax``` or  Applications » Utilities » Activity Monitor to check
* [launchd](https://www.soma-zone.com/LaunchControl/)

### Mac Pro upgrade
* [Mac Pro Upgrade guide](http://blog.greggant.com/posts/2018/05/07/definitive-mac-pro-upgrade-guide.html)


### 32 bit apps
```mdfind "kMDItemExecutableArchitectures == '*i386*' && kMDItemExecutableArchitectures != '*x86*'"```
from https://apple.stackexchange.com/questions/314460/how-to-identify-32bit-applications-on-macos-without-running-each-one

### Apple Sync Photo
Scenario: There are photos in my personal Pictures directory, and I would like to back it up to an External hard drive.  How would you do it? 
Pictures directory: /Users/you/Pictures
Harddrive directory: /Volume/MacBackup/Pictures

```
rsync -avzh /Users/you/Pictures /Volume/MacBackup/Pictures
```

* https://www.willhaley.com/blog/rsync-filters/ Using rsync filters 


###
```
codesign --remove-signature
xattr -cr /path/to/your/program.app

hex2bin firmware.hex
strings firmaware.bin

```
* https://reverseengineering.stackexchange.com/questions/15006/approach-to-extract-useful-information-from-binary-file?rq=1
* https://reverseengineering.stackexchange.com/questions/8177/convert-mach-o-vm-address-to-file-offset?rq=1
* https://reverseengineering.stackexchange.com/questions/17262/binwalk-alternative?noredirect=1&lq=1


### Macbook maintainence
https://beetstech.com/blog/apple-proprietary-ssd-ultimate-guide-to-specs-and-upgrades#hdr-7
https://beetstech.com/blog/replacing-thermal-paste

### XCode
https://smallhacks.wordpress.com/2018/11/11/how-to-support-old-osx-version-with-a-recent-xcode/


### Credits
* https://superuser.com/questions/334597/enable-disable-startup-programs-script-services-on-a-mac
