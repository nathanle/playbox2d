# playbox2d
A port of [box2d lite](https://github.com/erincatto/box2d-lite) to C for the [Playdate SDK](https://play.date/dev/).
...and a fork of: https://github.com/mierau/playbox2d

## Step 1
This a version that works in Linux (I am using Fedora 43).

If you get an error like this: `/usr/local/bin/arm-none-eabi-gcc: No such file or directory`
You will need to install `gcc-arm-none-eabi`

In Fedora, that was the following dnf command:
sudo dnf install arm-none-eabi-gcc-cs arm-none-eabi-gcc-cs-c++ arm-none-eabi-newlib



## Step 2
If you have installed the playdate SDK, you should have the following env var:
```
❯ env |grep -i playdate_sdk
PLAYDATE_SDK_PATH=/home/nathan/PlaydateSDK-3.0.6
```
The Makefile is going to use that information, so if you do not have it set, set it to point to the SDK on your system.


## Step 3
Then you just need to run `make` in the base path of this repo.

```
❯ make
detected_OS is "Linux"
mkdir -p build
mkdir -p build/dep
cp build/pdex.elf Source/
cp build/pdex.so Source/
/home/nathan/PlaydateSDK-3.0.6/bin/pdc -sdkpath /home/nathan/PlaydateSDK-3.0.6 Source playboxdemo.pdx
```

## Step 4
Then
```
❯ ./build_and_run.sh build

>> Attempting a build and run of PDX...
>> Cleaning build directory...
>> Building PDX with 'pdc'...
>> Running PDX with Simulator...
22:33:04: Loading: ./Builds/playbox2d.pdx/
Loading C API Library: ./Builds/playbox2d.pdx/pdex.so
22:33:04: SDK: /home/nathan/PlaydateSDK-3.0.6
22:33:04: Release: 3.0.6
22:33:04: CMD: ./Builds/playbox2d.pdx 
PBArray: creating with item size 8
PBArray: creating with item size 8
PBArray: creating with item size 152
```
