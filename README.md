# Makefiles
==========================

One [Makefile](./v3/Makefile) to rule them all.

### Project Layout for your project

```
anahata
 |
 |_ src/main/native/src 
 |
 |_ src/main/native/include (place all your header files and folders containing header files)
 |
 |_ bin (contains the binaries and final binary)
```

Place all your source file folders in the src directory. You can even created nested folders
with source files and the makefile will automatically detect it for you. Place all header files
in the include folder. The bin contains all the binaries and final executable.


