# swift-hello

A basic Swift program to test building for various platforms.

## Android
### CMake:
```cmd
cmake -B build -S . -G Ninja ^
    -D CMAKE_BUILD_WITH_INSTALL_RPATH=YES ^
    -D CMAKE_SYSTEM_NAME=Android ^
    -D CMAKE_ANDROID_ARCH_ABI=arm64-v8a ^
    -D CMAKE_SYSTEM_VERSION=29 ^
    -D CMAKE_Swift_COMPILER_TARGET=aarch64-unknown-linux-android29 ^
    -D CMAKE_Swift_FLAGS="-sdk %SDKROOT%\..\..\..\..\Android.platform\Developer\SDKs\Android.sdk -Xclang-linker -resource-dir -Xclang-linker %ANDROID_NDK_ROOT%\toolchains\llvm\prebuilt\windows-x86_64\lib\clang\17.0.2 -Xcc -I%SDKROOT%\..\..\..\..\Android.platform\Developer\SDKs\Android.sdk\usr\include"
cmake --build build
```
### Swift Build:
```
swift build --triple aarch64-unknown-linux-android29 ^
    --sdk %ANDROID_NDK_ROOT%\toolchains\llvm\prebuilt\windows-x86_64\sysroot ^
    -Xswiftc -I -Xswiftc %SDKROOT%\..\..\..\..\Android.platform\Developer\SDKs\Android.sdk\usr\include ^
    -Xswiftc -sdk -Xswiftc %SDKROOT%\..\..\..\..\Android.platform\Developer\SDKs\Android.sdk ^
    -Xswiftc -sysroot -Xswiftc %ANDROID_NDK_ROOT%\toolchains\llvm\prebuilt\windows-x86_64\sysroot ^
    -Xswiftc -Xclang-linker -Xswiftc -resource-dir -Xswiftc -Xclang-linker -Xswiftc %ANDROID_NDK_ROOT%\toolchains\llvm\prebuilt\windows-x86_64\lib\clang\17.0.2
```
