# Protobuf Matlab

protobuf-matlab - FarSounder's Protobuf compiler for Matlab
Copyright 2011 FarSounder, Inc.
http://code.google.com/p/protobuf-matlab/


## Overview

This package provides a Matlab code generator for version 3.11.0 of Google's
Protocol Buffers compiler (protoc) as well as support libraries for the
generated Matlab code.


## Building protoc with Matlab support

1. Get the protobuf source:
```
git clone https://github.com/protocolbuffers/protobuf.git
```

2. Get the protobuf-matlab source:
```
git clone https://github.com/farsounder/protobuf-matlab.git
```

3. Add the protobuf-matlab src files to the Google Protobuf src:
```
cp -r protobuf-matlab/{src} protobuf
```

4. Compile the modified protobuf for:
```
cd protobuf/cmake
git submodule update --init --recursive
mkdir build && cd build
cmake ..
make
sudo make install
```


## COMPILE USING WINDOWS

for Windows use MSYS2 MinGW64 shell and run:
install mingw-w64-x86_64-cmake and mingw-w64-x86_64-ninja by
open msys2 shell and run
```
pacman -S mingw-w64-x86_64-cmake
pacman -S mingw-w64-x86_64-ninja
 ```
:warning: NOW RENAME OR DELETE THE FILE install_dir/msys64/usr/lib/librt.a e.g. to librt.bak 
then run
```
cd ~
git clone https://github.com/protocolbuffers/protobuf.git
git clone https://github.com/ConverterLabs/protobuf-matlab.git
cd protobuf/cmake
git submodule update --init --recursive
```
copy the src folder from protobuf-matlab to protobuf
```
cp -r ~/protobuf-matlab/src ~/protobuf
```
then run
```
mkdir build && cd build
cmake -G Ninja ~/protobuf -DCMAKE_BUILD_TYPE=Release
cmake --build ./
```

This should yield a protoc executable with a --matlab_out option. You can now
use protoc to generate Matlab reading and writing code for your .proto file(s).

```
protoc test.proto --matlab_out=./
protoc test_import.proto --matlab_out=./
```

Test by 
```
pb_run_test
```

## Matlab support library setup

In order to use the generated Matlab code, you'll need to add the protobuflib
directory to your Matlab path. protobuflib is a collection of .m utility files
used by the generated code.
