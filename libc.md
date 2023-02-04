Understanding the lib c is important as it is tightly integrated with kernel under it. And the C library with the corresponding C compiler determines the functionalities of the operating system.

Some famous examples.

* major Linux distribution ( e.g. Ubuntu, Centos, Redhat OS) and glibc
* FreeBSD and lib C
* Android and bionic C library
* Solaris and lib C
* Alpine Linux and musl C library
* openwrt (e.g. embedded Linux) and musl C library
* TempleOS and holyC compiler and corresponding libraries.


There had been multiple experiments to build the kernel using a different libraries.  It is doable, but it requires a herculean efforts to undertake such exercise.  The issue is there are missing functionalities within the libraries and they need to be backported to the other systems.

The other issue is the applications running on top of the kernel needs to use library too. When you port an application to a new OS, it needs to port all the API functionalities and library dependencies to the system. And there had been multiple ways to do it.

* port the underlying libraries to the new operating system, and compile the application using the ported library.
* rewrite the application to use the libraries ties to the OS, and port missing functionalities and API as required.
* capture all the underlying dependencies and ship the application as a unikernel application. e.g. SQL server running in Linux using drawbridge technology. see https://arstechnica.com/information-technology/2016/12/how-an-old-drawbridge-helped-microsoft-bring-sql-server-to-linux/

Here are some examples:

* https://unix.stackexchange.com/questions/34650/is-the-solaris-libc-based-on-the-gnu-libc
* https://forum.openwrt.org/t/how-to-use-the-musl-c-library-instead-of-uclibc/29658
* https://unix.stackexchange.com/questions/36267/can-i-build-a-linux-distro-with-libc-instead-of-glibc
* https://lists.debian.org/debian-bsd/2003/01/msg00013.html  good comparison of glibc and freebsd libc
* https://arstechnica.com/civis/viewtopic.php?f=20&t=198967
* https://docs.oracle.com/cd/E36784_01/html/E36873/libc-3lib.html Solaris libc
* https://stackoverflow.com/questions/21082738/why-use-a-different-c-library
* https://www.reddit.com/r/linux/comments/678be3/which_c_library_is_used_by_the_bsd_systems/
* https://stackoverflow.com/questions/59019932/what-standard-c-library-does-clang-use-glibc-its-own-or-some-other-one
* https://www.linux.org/threads/a-variety-of-c-standard-libraries.11419/
* https://eerielinux.wordpress.com/2014/04/01/arche5-ditches-eglibc-and-goes-for-musl-libc/
* https://blogs.oracle.com/solaris/weakfilters-v2
* https://www.reddit.com/r/C_Programming/comments/cx55zr/where_to_start_with_writing_my_own_libc/
* https://www.gnu.org/software/libc/sources.html
* https://github.com/Biolunar/liblinux

Some comparisons of the libraries
* https://wiki.osdev.org/C_Library
* https://elinux.org/images/8/8b/Room_For_Cooperation-_Bionic_and_musl.pdf
* https://events.static.linuxfound.org/sites/events/files/slides/libc-talk.pdf


ToolChain
* https://fosdem.org/2021/schedule/event/toolchains_choice/

There are also other requirement when porting applications due to system differences.
* Windows scatter/gather IO vs Linux vectored IO

The other approach is to run the applications in emulated mode. There are many tools for virtualization (e.g. wine, qemu, kvm, wsl and many others.  and one can read the notes on virtualizations


### C++ library
http://stdcxx.apache.org/download.html
https://www.incredibuild.com/blog/top-13-c-libraries-to-watch-out-for
https://www.incredibuild.com/blog/what-is-a-virtual-function virtual function
