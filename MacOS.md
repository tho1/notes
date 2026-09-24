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


### menu
defaults write com.apple.dt.Xcode ShowDVTDebugMenu -bool YES
sudo mkdir -p /Applications/Xcode.app/Contents/Developer/AppleInternal/Library/Xcode
sudo touch /Applications/Xcode.app/Contents/Developer/AppleInternal/Library/Xcode/AppleInternal.plist


### 
https://trac.macports.org/ticket/62426   libc++: using a newer libc++ to build software on older macos systems

# Don't forget to restart Xcode

### Mavericks 10.9
https://apple.stackexchange.com/questions/402726/how-can-i-attempt-to-boot-an-older-version-of-macos-than-my-hardware-supports/402727#402727
https://gist.github.com/kimmobrunfeldt/350f4898d1b82cf10bce [Install web development tools to Mavericks (OS X 10.9)]


### Macbook maintainence
https://beetstech.com/blog/apple-proprietary-ssd-ultimate-guide-to-specs-and-upgrades#hdr-7
https://beetstech.com/blog/replacing-thermal-paste   

### Airdrop for older mac
defaults write com.apple.NetworkBrowser BrowseAllInterfaces 1 see https://www.funkyspacemonkey.com/airdrop-work-older-macs

### disable discrete card
https://discussions.apple.com/thread/8161951?sortBy=rank
https://gist.github.com/cdleon/ae1542279598fe80f527400cc354a956?permalink_comment_id=4902254
sudo pmset -a gpuswitch 0 

### XCode
https://smallhacks.wordpress.com/2018/11/11/how-to-support-old-osx-version-with-a-recent-xcode/

### syscall related info
https://stackoverflow.com/questions/14370328/where-is-syscall-sw-h-in-mac-os-x

### M1 Mac OS X assembly sample
https://gist.github.com/zeusdeux/bb5b5b0aac1a39d4f9cec0d4f9a44ffb

### Credits
* https://superuser.com/questions/334597/enable-disable-startup-programs-script-services-on-a-mac

