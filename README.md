# cabman
Stand-alone / separate version of cabman - ReactOS cabinet manager 

The code was taken from the ReactOS project for further improvement and reusability in other projects. 

Build with CMake: 

Linux build:  
``` 
mkdir build && cd build
cmake -G "Unix Makefiles" ..
make
```  
MinGW or MXE Cross-compiling:  
```
mkdir build && cd build
cmake -G "Unix Makefiles" .. -DCMAKE_TOOLCHAIN_FILE=Your-CrossCompiling-Toolchain-file.cmake
make
```
