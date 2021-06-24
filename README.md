Guide for installing optimized Minecraft Java on Raspberry Pi
================

## Step 1: Hardware

You should have at least a Raspberry Pi 3 module or you won't get Minecraft running at adorable performance.     
I recommend at least Reaspberry Pi 4 with 2 GB of Ram.

IMPORTANT: A fast SD-card or USB-stick is neccasary to run Minecraft and the whole system and a fast speed. Using a slow device will let your system hang sometime.

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
Now check the output of `uname -p`:

For armhf/armv7:
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
Arm devices cant run the newest Minecraft Java launcher so we have two Options:

launcher | official legacy launcher | MultiMC5 launcher
--- | --- | ---
Mojang Account support | yes | yes
Microsoft Account support | no | yes
Pros | easier to handle | -
Cons | - | needs to get build (needs some time)

> only install one of the launcher (you can choose on your one which you will use)

I. legacy launcher
a) Downlod it
```
cd ~/Minecraft && wget https://launcher.mojang.com/v1/objects/eabbff5ff8e21250e33670924a0c5e38f47c840b/launcher.jar
```
b) Add Minecraft to software list:
```
nano ~/.local
```
And add following content:
``` 
test
```
Save with crtl+o, enter, ctrl+x


II. MultiMC
a) Download build files:
```
mkdir ~/MultiMC && cd ~/MultiMC
mkdir build && mkdir install
git clone --recursive https://github.com/MultiMC/MultiMC5.git src
```
b) Build and install MultiMC5
```
cd build
cmake -DCMAKE_INSTALL_PREFIX=../install ../src
make -j4 install
```

## Step 4: Setup launcher

I. Legacy launcher  
a) Start launcher and login to your Account 
b) You need to create a new installation. You can select every Version ( even alpha/beta and experimental)   
You need to add the following line at "jvm-options" at the end
```
-
```
c) save the installation and start it

II. MultiMC5

## Step 5: Install optimizing mods  
There are two Options:
Mod | Optifine | Sodium
-|-|-
Version | 1.0 - 1.17 | 1.16
Pro | more Options | more FPS

I. Sodium (1.16 only)  
a) Install fabric mod loader  
A window will popup, choose version 1.16.5 and hit enter  
```
wget https://maven.fabricmc.net/net/fabricmc/fabric-installer/0.7.4/fabric-installer-0.7.4.jar && java -jar  fabric-installer-0.7.4.jar
```
b) Install mods
```
mkdir ~/.minecraft/mods && cd ~/.minecraft/mods && wget https://media.forgecdn.net/files/3067/101/sodium-fabric-mc1.16.3-0.1.0.jar && wget https://media.forgecdn.net/files/3294/303/phosphor-fabric-mc1.16.3-0.7.2%2Bbuild.12.jar && wget https://media.forgecdn.net/files/3344/974/lithium-fabric-mc1.16.5-0.6.6.jar
```
c) start minecraft and edit the jvm options again (add the following at the end)
```
-
```

II. Optifine

a) Download your preferred Version at http://optifine.net/downloads

b) Run the following command to install Optifine. Replace "Optifine.jar" with the name of your file.  
A window will popup, hit install.
```
java -jar Optifine.jar
```

c) start minecraft and edit the jvm options again (add the following at the end)
```
-
```

d) start Optifine and be happy :)

## Step 6: Optimize system (optional)

a) Overclock (cooling is very recommend)   
Edit the boot config file...
```
sudo nano /boot/config.txt
```
... and add the following line (reboot needed):
```
over_voltage=6
arm_freq=2000
gpu_freq=700
```


b) Use lightwight Desktop
The default Raspberry Pi OS Desktop "PIXEL" is already pretty lightweight. Alternative you can use xfce4 or lxqt:
```
sudo apt installl xfce4 -y
---
sudo apt install lxqt-desktop -y
```

c) Remove unnecassary backround services
