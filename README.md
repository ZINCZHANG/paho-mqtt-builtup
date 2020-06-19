# paho-mqtt-builtup

## Build and Install the Paho C library from source (as Paho C++ is a wrapper that call the C-library functions)

clone the reposity
  
  
```
git clone https://github.com/eclipse/paho.mqtt.c.git
```
  
  
go to the directory
  
```
cd paho.mqtt.c
```
  
checkout
  
```
git checkout v1.3.1
```
  
make sure to generate the makefiles with the "PAHO_BUILD_STATIC" flag ON as the libraries will be linked as static libraries, before run cmake, add the following commands in the CMakeCache.txt located in build folder
	
```
// position independent code flag
CMAKE_POSITION_INDEPENDENT_CODE:BOOL=TRUE)
```
  
run cmake
  
```
cmake -Bbuild -H. -DPAHO_WITH_SSL=ON -DPAHO_ENABLE_TESTING=OFF -DPAHO_BUILD_STATIC=ON ()
```
  
(Need to have libssl-dev installed)
build
  
```
sudo cmake --build build/ --target install
```
  
done
  
```
sudo ldconfig
```

## Build and Install the Paho C++ library from source

clone the reposity 
  
  
```
git clone https://github.com/eclipse/paho.mqtt.cpp
```

go to directory

```
cd paho.mqtt.cpp
```

make sure to generate the makefiles with the "PAHO_BUILD_STATIC" flag ON as the libraries will be linked as static libraries, before run cmake, add the following commands in the CMakeCache.txt located in build folder

```
// position independent code flag
CMAKE_POSITION_INDEPENDENT_CODE:BOOL=TRUE
```

run cmake

```
cmake -Bbuild -H. -DPAHO_BUILD_DOCUMENTATION=FALSE -DPAHO_BUILD_SAMPLES=TRUE -DPAHO_BUILD_STATIC=TRUE 
```

run install

```
sudo cmake --build build/ --target install
```
One problem encountered, relocation R_X86_64_PC32 against symbol `MQTTAsync_start_clock' can not be used when making a shared object; recompile with -fPIC, this would be able to solve it

```
// position independent code flag
CMAKE_POSITION_INDEPENDENT_CODE:BOOL=TRUE)
```

done

```
sudo ldconfig 
```
