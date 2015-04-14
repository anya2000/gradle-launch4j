# Introduction #

The two native executables distributed with launch4j (ld and windres) are PPC and with Lion, Apple has remove the ability to emulate the PPC on an Intel processor. So, Launch4J will not run out of the box on Lion.

However, it is easy to recompile ld and windres and replace them in the Launch4J distribution.


# Details #

Download the latest binutils (2.22 as of 7 Feb 2012) from http://www.gnu.org/software/binutils/.

```
tar zxf binutils-2.22.tar.gz
cd binutils-2.22
./configure --target=i686-pc-mingw32
make
cp binutils/windres /whereever_you_installed/launch4j/bin/.
cp binutils/ld/ld-new /whereever_you_installed/launch4j/bin/ld
```

The new ld and windres should now work with Launch4J on Lion. Note that ld seems to be compiled to **ld-new** by default in binutils, so you need to make sure you rename as well as copying to the correct location.