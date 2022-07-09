Compiler 

Mix and matching the C library with the compiler 

compiler and libraries in general 
* https://softwareengineering.stackexchange.com/questions/214108/how-small-is-the-footprint-of-a-small-c-compiler
* [compiler comparision](https://colfaxresearch.com/compiler-comparison/)
* https://softwareengineering.stackexchange.com/questions/359576/what-is-actually-the-difference-between-the-gnu-c-library-and-the-c-standard-lib
* http://www.etalabs.net/compare_libcs.html
* https://softwareengineering.stackexchange.com/questions/273698/why-are-there-so-few-c-compilers/273711#273711
* [C Is Not a Low-level Language](https://queue.acm.org/detail.cfm?id=3212479)
* https://wiki.archlinux.org/title/C

### TCC
* [Building SDL2 applications with TCC, The Tiny C Compiler, on Windows](https://www.youtube.com/watch?v=HIV62ato9iA)
* [tcc and dietlibc](https://www.monperrus.net/martin/compiling-c-code-with-dietlibc-and-tcc) 
* [where is function "_start"?](https://www.monperrus.net/martin/compiling-where-is-_start)
* [tcc with uClibc](https://github.com/pts/pts-tcc)
* TCC uses the libdef to figure out how to call a windows dll. One needs to use tcc to generate .def file from a dll, and then call the required functions.  It would be interesting to use it get the list of functions used in a dll.


### TCC and dietlibc integrations.
in config.mak
```
  CFLAGS=-I/usr/include/diet/ -D__dietlibc__ -DCONFIG_TCC_STATIC 
  LDFLAGS=-L/usr/lib/diet/lib/ -nostartfiles
```
CONFIG_TCC_STATIC says that dynamic loading (libdl) should not be used. However, there is a dependency to libdl at linking time (-ldl).

In `Makefile’:
```
remove LIBS+=-ldl.
add crt0.o to linked objects ` $(CC) -o $@ crt0.o $^ $(LIBS) $(CPPFLAGS) $(CFLAGS) $(LDFLAGS) $(LINK_LIBTCC)

```
crt0.o is the startup file which provides function _start as entry point.
Function _start of dietlibc is in a file called start.o. We copy it to crt0.o 
```

  $ cp /usr/lib/diet/lib/start.o crt0.o

```

see https://www.monperrus.net/martin/compiling-tcc-with-dietlibc 

#### TCC and the libraries
TCC excels at compiling speed,  as it does not perform as much compiler optimization as GCC.  It would be interesting to see the libraries that work with the TCC.  GCC had a lot of include files that are specific to the Linux kernel, which explains the high correlation between GCC and Linux kernel.  Therefore, TCC would be a good candidate for testing the other size optimized libraries.  It is always interesting to see that one can compile C source code with a size optimized compiler.  The only downside is binary generated might not be speed optimized as other C compiler.

It is still a good compiler for educational purpose.  One can read the source code of TCC, as it include the work preprocessor, compiler, linker all in one binary.

Links above provide TCC with ulibC and TCC with dietlibc

### TCC and dietlibc
There is work that one tries to recompile TCC using dietlibc. Interesting exercise.  It would be good to create some benchmark for comparison.

Here are some tips for compiling code using dietlibc.
```
CC="diet gcc -nostdinc -D_BSD_SOURCE " \
CFLAGS=" -pipe -combine -Os -ffunction-sections -fdata-sections -momit-leaf-frame-pointer -fomit-frame-pointer -mpreferred-stack-boundary=2 -fmerge-constants " \
LDFLAGS=" -Wl,-O,--gc-sections " \
./configure --prefix=/opt/diet --disable-nls --help
```
see https://oldforum.puppylinux.com/viewtopic.php?t=44737


### musl 
* https://superuser.com/questions/1219609/why-is-the-alpine-docker-image-over-50-slower-than-the-ubuntu-image
* https://developers.home-assistant.io/blog/2020/07/13/alpine-python/
* https://www.reddit.com/r/rust/comments/gdycv8/why_does_musl_make_my_code_so_slow/ jemalloc is the solution
* https://github.com/flamegraph-rs/flamegraph use flamegraph to monitor

### code checker
https://www.frama-c.com/

### performance
http://www.brendangregg.com/blog/index.html

### GCC vs CLang
https://alibabatech.medium.com/gcc-vs-clang-llvm-an-in-depth-comparison-of-c-c-compilers-899ede2be378

### GCC compilation
https://iamsorush.com/posts/build-gcc11/

### GCC supported features.
```gcc -v --help 2> /dev/null | sed -n '/^ *-std=\([^<][^ ]\+\).*/ {s//\1/p}'```

### LLVM 

### Simple C compiler
[simple C, use QBE](http://www.simple-cc.org/)


### QBE
* compiler backend [https://c9x.me/compile/]  
