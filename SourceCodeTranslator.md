### synopsis
It is part of the token parser, similar to the source code analyser, but skip the part on turning out the object code like a compiler.  Instead it produces the source code. Furthermore, some compiler also produce the assembly code. 

What about the tools that helps to browser source code like ctags and cscope?  They also implement some of the functionalites too.

### online
https://www.carlosag.net/tools/codetranslator/

### examples
https://github.com/ivmai/JCGO
bacon Basic to C 
[toba](https://www2.cs.arizona.edu/projects/sumatra/toba/benchmarks.html)

### thoughts

https://www.reddit.com/r/csharp/comments/49daud/converting_this_from_java_to_c/


### many different type of translator.
https://en.wikipedia.org/wiki/Translator_(computing)


### source code walkthrough and search


#### cscope

* select the files to be added.


```
find . -name "*.c" -o -name "*.cpp" -o -name "*.h" -o -name "*.hpp" > cscope.files
cscope -q -R -b -i cscope.files
cscope -d
```

#### cscope for linux kernel

```
#!/bin/bash

LNX="."

echo "Finding relevant source files..."
find $LNX                                                                \
    -path "$LNX/arch/*" ! -path "$LNX/arch/x86*" -prune -o               \
    -path "$LNX/include/asm-*" ! -path "$LNX/include/asm-generic*"       \
                               ! -path "$LNX/include/asm-x86*" -prune -o \
    -path "$LNX/tmp*" -prune -o                                          \
    -path "$LNX/Documentation*" -prune -o                                \
    -path "$LNX/scripts*" -prune -o                                      \
    -name "*.[chxsS]" -print > $LNX/cscope.files

echo "Building cscope database..."
time cscope -q -k -b -i cscope.files

exit 0
```

#### cscope tips.
* -C disables case-sensitive search (this can also be toggled from within Cscope with Ctrl-c).
* -p4 causes Cscope to prepend the directories (up to 4) leading to a source file in your tree when displaying its results.
* Pressing Ctrl-b allows you to search for previous search terms again.


Reference: https://courses.cs.washington.edu/courses/cse451/12sp/tutorials/tutorial_cscope.html
