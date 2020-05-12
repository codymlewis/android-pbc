# PBC for Android
PBC pre-built for the android platform

## Using this
Add this repository as submodule to your program with something like the
following:
```sh
git submodule add git://github.com/codymlewis/android-pbc.git app/src/main/cpp/pbc
```

then add the following in your cmake file somewhere after the
`cmake_minimum_required` line:
```cmake
add_library(pbc SHARED IMPORTED)
set_target_properties(pbc PROPERTIES IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/pbc/${ANDROID_ABI}/libpbc.so)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/pbc/include/)
```

and add `pbc` to your `target_link_libraries` in the same cmake file, for
example:
```cmake
target_link_libraries(native-lib pbc ${log-lib})
```

## How-to: Build your own version
### Requirements
- Android SDK
- Android NDK
You must also set the `ANDROID_NDK_ROOT` variable to the location of the root of
you ndk folder and set `ANDROIDAPI` the integer version of the api you are
using.

You will also want a copy of the [GMP](https://gmplib.org) library built for android, for example,
through cloning with the following:
```sh
git clone https://github.com/Rupan/gmp.git
```

### Building
Get pbc and move into the directory:
```sh
git clone https://github.com/blynn/pbc
cd pbc
```

Now run a compiling script, you may need to modify it for your setup:
```sh
../build-scripts/compile-all
```
