vim tips and tricks.

https://stackoverflow.com/questions/53664/how-to-effectively-work-with-multiple-files-in-vim?rq=1

### vim tutorial
https://github.com/mhinz/vim-galore 


### vim plugins
* [for sysadmin](https://www.redhat.com/sysadmin/five-vim-plugins)
* [for dev](https://opensource.com/article/19/1/vim-plugins-developers)


### ctags
https://kulkarniamit.github.io/whatwhyhow/howto/use-vim-ctags.html

add the following to ~/.ctags
```
--recurse=yes
--exclude=.git
--exclude=BUILD
--exclude=.svn
--exclude=*.js
--exclude=vendor/*
--exclude=node_modules/*
--exclude=db/*
--exclude=log/*
--exclude=\*.min.\*
--exclude=\*.swp
--exclude=\*.bak
--exclude=\*.pyc
--exclude=\*.class
--exclude=\*.sln
--exclude=\*.csproj
--exclude=\*.csproj.user
--exclude=\*.cache
--exclude=\*.dll
--exclude=\*.pdb
```

go to the source code directory, run ctags.


cscope


### Derivative
* https://github.com/SpaceVim/SpaceVim
* https://github.com/neovim/neovim
* https://github.com/onivim/oni2

### Reference
https://github.com/mhinz/vim-galore
