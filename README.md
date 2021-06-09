Guide for installing optimized Minecraft Java on Raspberry Pi
================

## Step 1: Hardware

You should have at least a Raspberry Pi 3 module or you won't get Minecraft running at adorable performance.     
I recommend at least Reaspberry Pi 4 with 2 GB of Ram.

## Step 2: Software
1. Install dependencies
```
sudo apt install openjdk-8-jre wget
```
2. Install LWJGL locally
 > Minecraft does not ship LWJGL for arm devices in their laucher so we need to manuelly install them
```
cd ~ && mkdir -p Minecraft/lwjgl && cd Minecraft/lwjgl
```
No check the output of `uname -p`:

For armhf:
```
wget xy.com && tar -xvf lwjgl2-linux-arm32.tar.gz --one-top-level=v2
wget xy.com && tar -xvf lwjgl3-linux-arm32.tar.gz --one-top-level=v3
```
For aarch64:
```
wget xy.com && tar -xvf lwjgl2-linux-arm64.tar.gz --one-top-level=v2
wget xy.com && tar -xvf lwjgl3-linux-arm64.tar.gz --one-top-level=v3
```

## Step 3: Install the Launcher
Arm devices cant run the newest Minecraft Java launcher so we have to Options:

launcher | a) official legacy launcher | b) MultiMC5 launcher
--- | --- | ---
Mojang Account support | yes | yes
Microsoft Account support | no | yes
Pros | easier to handle | -
Cons | - | needs to get build (needs some time)

> only install one of the launcher (you can choose on your one which you will use)

a) legacy launcher
```
cd ~/Minecraft && wget https://launcher.mojang.com/v1/objects/eabbff5ff8e21250e33670924a0c5e38f47c840b/launcher.jar
```
