This file is an endeavour to look at some company that goes out of certain industry that they use to be a leader.
Looking back at history is an interesting way to study how certain technology mature, and turn into something no one expected.


### Apple Printers

* [Why doesn't Apple build a printer?](https://www.quora.com/Why-doesnt-Apple-build-a-printer) 
* [Why Apple got out of the laser printer business](https://talk.tidbits.com/t/why-apple-got-out-of-the-laser-printer-business/4707)

### Apple Bandai Pippin
* [Apple Bandai Pippin](https://en.wikipedia.org/wiki/Apple_Bandai_Pippin)

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

### Ipad air ghost type issue
https://www.ifixit.com/Answers/View/192265/solution+to+phantom-ghost+touches+ipad+air
https://www.ifixit.com/Answers/View/137418/Digitizer+freaks+out+when+laid+flat+on+the+frame
https://imgur.com/a/mwTJa

### Macbook maintainence
https://beetstech.com/blog/apple-proprietary-ssd-ultimate-guide-to-specs-and-upgrades#hdr-7
https://beetstech.com/blog/replacing-thermal-paste

### XCode
https://smallhacks.wordpress.com/2018/11/11/how-to-support-old-osx-version-with-a-recent-xcode/
