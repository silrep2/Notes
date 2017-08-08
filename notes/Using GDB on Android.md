# How to gdb on android
## Preparation
**Download tooltains**

download `android-ndk-r10e`, assuming placed in `~/`

**Put gdb on phone**

```bash
adb  push  ~/android-ndk-r10e/prebuilt/android-arm64/gdbserver/gdbserver  /sdcard/mytools
```

**Set arm-gdb as environment var**

```bash
export armv8-gdb=~/android-ndk-r10e/toolchains/aarch64-linux-android-4.9/prebuilt/linux-x86_64/bin/aarch64-linux-android-gdb
echo "export armv8-gdb=~/android-ndk-r10e/toolchains/aarch64-linux-android-4.9/prebuilt/linux-x86_64/bin/aarch64-linux-android-gdb" >> ~/.profile
```

## If Phone conntected by USB

**Open one terminal**

```bash
adb push /exe/path/on/pc /exe/path/on/phone
adb shell
/sdcard/mytools/gdbserver :1234 /exe/path/on/phone
# you can replace 1234 with any available port
```

**Open another terminal**

```bash
adb  forward tcp:1234  tcp:1234
$armv8-gdb /exe/path/on/pc
target remote localhost:1234
```

## If connect remote Phone

Using IP addr to connect each other.
You can use `ping` command to test if they are connected.

**Terminal on phone**
```bash
/sdcard/mytools/gdbserver 192.168.0.pc:1234 
```

**Terminal on PC**

```bash
$armv8-gdb /exe/path/on/pc
target remote 192.168.0.phone:1234
```











