# Android NDK r7b with host modules (and MIPS) support (>100MB)

Google's Android NDK only support target (device-specific modules).

Li Zheng <flyskywhy@gmail.com> added host support on 2012.05.07:

- Add host executable module support
- Add host static library module support
- Add host support by MinGW under Windows (recommend msys.bat in [msysgit](http://github.com/msysgit/msysgit))
- Add host support by MinGW under Linux (recommend `apt-get install gcc-mingw32` and use below command to install `mingw32-zlib`)

`wget http://apt.arrozcru.org/mingw32-zlib/mingw32-zlib_1.2.5-1_all.deb; sudo dpkg -i mingw32-zlib_1.2.5-1_all.deb`

# The build environment

You can use below command from [android-apps-host](http://github.com/flyskywhy/android-apps-host) to compile:

`compile.sh`

If your app need contents from AndroidConfig.h (e.g. on linux host, adb.c need HAVE_FORKEXEC), please `export ANDROID_SYS_HEADERS` like `compile.sh`

if your app need ld to some .a files (e.g. on linux host, adb need libcutils.a, you can get the .a files from compiled Android source or modify and run `host-libs/gen-libs.sh` from [android-apps-host](http://github.com/flyskywhy/android-apps-host)), please put them to `export HOST_LIBS=${PWD}/host-libs` folder described in `compile.sh` 
