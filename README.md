# Makefiles
==========================

Writing makefiles was a difficult and painful process for me. Makefiles is a project which brings you one grand unified Makefile that can be used across all your projects without having to change the Makefile everytime you add a source file or a header file or a new folder.


One [Makefile](./v3/Makefile) to rule them all.

### Directory Layout for your project

```
anahata
 |
 |_ src/main/native/src 
 |
 |_ src/main/native/include
 |
 |_ bin
```

Place all your source file folders in the src directory. You can even created nested folders
with source files and the makefile will automatically detect it for you. Place all header files
in the include folder. The bin contains all the binaries and final executable.


