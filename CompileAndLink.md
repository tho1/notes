### Introduction

Maintaining a system always take a lot of work.  One needs to read the documentation and figure out the multiple steps involved.  There are many tools involved.

How to pass parameters to change the install path?
32 and 64 bit location


#### These command are configure related.
autoconf
libtoolize
aclocal
autoheader


#### autoconf
autoconf generates the configuraition file

#### M4
M4 is the macro that used to define the make file and directories.


#### configure
Configure --help

#### cmake
cmake -DLIB_SUFFIX=64 This defines the library should be saved in /usr/local/lib/lib64.  Default is /usr/local
https://stackoverflow.com/questions/6241922/how-to-use-cmake-install-prefix  change the cmake install prefix

