This stores the notes about the Android platform.

Android platform is based on Linux kernel, but it does not use glibc library due to GNU license issue.  It uses the bionic C library instead of glibc library.

* https://stackoverflow.com/questions/39108778/bionic-and-libc-s-stub-implementations
* https://stackoverflow.com/questions/33076206/how-to-add-libc-to-android-application
* https://stackoverflow.com/questions/36331048/compiling-gentoo-bionic-on-a-x86-64-linux-machine
* https://github.com/krisk0/pc-linux-android

Notes on building AOSP
* https://www.raywenderlich.com/10197539-building-the-android-open-source-project
* https://www.android-x86.org/source.html
* https://stackoverflow.com/questions/57863059/aosp-build-both-x86-and-x64-for-aosp-x86-64-eng
* https://stackoverflow.com/questions/35838183/compiling-ndk-library?rq=1


Android tools in Ubuntu
* [Android development tools for Debian] (https://wiki.debian.org/AndroidTools)

Android code search
* https://cs.android.com/

### Android development
* [Top 10 Most Common Mistakes That Android Developers Make: A Programming Tutorial](https://www.toptal.com/android/top-10-most-common-android-development-mistakes)

### Understanding build layer and other concepts.
* https://source.android.com/setup/develop/new-device#build-layers
* https://source.android.com/setup/start/build-numbers#source-code-tags-and-builds

###
* https://www.reddit.com/r/Android/comments/ngphyi/some_useful_adb_commands_and_oneliners_for/ adb onliner

### Android logging
* https://android.stackexchange.com/questions/14430/how-can-i-view-and-examine-the-android-log
* https://android.stackexchange.com/questions/14430/how-can-i-view-and-examine-the-android-log

### battery health
* ```cat /sys/class/power_supply/battery/charge_full```
* ```cat /sys/class/power_supply/battery/battery_cycle``` 

### double tap
* https://www.android-examples.com/detect-double-tap-click-on-screen-in-android-programmatically/
* https://www.androidauthority.com/android-11-double-tap-tap-1143186/
* https://stackoverflow.com/questions/2217670/android-how-to-detect-double-tap
* https://www.makeuseof.com/tag/lock-unlock-android-device-power-button-broken/
* https://android.googlesource.com/platform/frameworks/base/+/master/core/java/android/view/GestureDetector.java
* https://nexus5.gadgethacks.com/how-to/enable-hidden-double-tap-wake-feature-your-nexus-6-0158746/



### apk related
* [apk studio](https://github.com/vaibhavpandeyvpz/apkstudio)
* [apk sites] (https://helpdeskgeek.com/free-tools-review/5-best-safe-apk-download-sites-for-android-apps/)

### building Marshmallow for Nexus S
* [How to build Android Marshmallow on Nexus S](http://dmitry.gr/?r=06.%20Thoughts&proj=05.%20Android%20M%20on%20Nexus%20S)

### Oneplus 6t related
* https://forum.xda-developers.com/f/oneplus-6t-roms-kernels-recoveries-other-dev.8261/
* [oneplus 6T kernel QualComm SDM845 SOC](https://github.com/0ctobot/neutrino_kernel_oneplus_sdm845)
* https://androidfilehost.com/?w=files&flid=287218
* https://www.xiaomidriversdownload.com/oneplus-adb-drivers-for-windows/  oneplus adb driver
* https://forum.xda-developers.com/c/oneplus-6t.8257/
* [Customize the 6T kernel](https://forum.xda-developers.com/t/how-to-customize-the-kernel-of-oneplus-6t.3930896/)
* [Restore Bricked OnePlus 6T on Linux](https://forums.ubports.com/topic/5715/restore-bricked-oneplus-6t-on-linux)
* [fajita factory flash](https://github.com/Intrinsically-Sublime/fajita-factory-flash-bash-scripts)
* [list of phones using same 845 SOC](https://www.techwalls.com/qualcomm-snapdragon-845-smartphones/)

### Oneplus 7
* https://forums.oneplus.com/threads/how-to-roll-back-to-android-10-on-oneplus-7-pro-from-oos11-open-beta-4.1413325/
* https://www.reddit.com/r/oneplus/comments/nkp4g2/oneplus_7_oxygen_os_11011gm57aa_update/
* https://www.reddit.com/r/oneplus/comments/niy17q/oxygen_os_11011_update_bug/
* https://forums.oneplus.com/threads/rollback-from-stable-android-11-to-stable-android-10.1415135/
* https://www.droidwin.com/rollback-oneplus-7-7t-pro-android-10-oxygenos-10/ downgrade

### Asus zenfone 2 zoom

### ASUS zenfone 4 max
* https://www.androidinfotech.com/root-asus-zenfone-4-max-oreo/
* https://forum.xda-developers.com/c/asus-zenfone-4-max.6884/\
* https://www.getdroidtips.com/lineage-os-17-1-asus-zenfone-4-max/  install LineageOS 17.1
* https://forum.xda-developers.com/t/rom-unofficial-lineageos-17-1-for-asus-zenfone-4-max-q-zc520kl-zc554kl.4089735/
* https://zentalk.asus.com/en/discussion/40087/solved-zenfone-4-max-zc554kl-camera-not-working-dark take it apart!?
* https://www.youtube.com/watch?v=4Uh8Ecw9i_A replace LCD
* https://www.youtube.com/watch?v=iOIZTq4YRDc zenfone 4 max disassembly
* https://www.youtube.com/watch?v=DkYHgubOhqs root
* https://www.asus.com/ca-en/supportonly/ZenFone4%20Max%20(ZC554KL)/HelpDesk_BIOS/ official support link
* https://forum.xda-developers.com/t/guide-how-to-unlock-bootloader-zc554kl-do-with-your-own-risk.3677270/
* Android AOSP version Version WW-AOSP-16.0200.1907.28 Android 9 Pie.  Build Number: PKQ1.181203.001.WW_Phone-16.0200.1907.28-20190708
* https://zenfonekit.weebly.com/zenfone-4-max-zc554kl.html list of ASUS ROMS releases 

### camera related
* https://www.jianshu.com/p/bb048e5d8aa3
* https://www.jianshu.com/p/1f7da4a05b4e
* https://blog.csdn.net/liwei16611/article/details/53955711
* open camera Mark Harman
* camera test https://www.apk20.com/apk/1827662/
