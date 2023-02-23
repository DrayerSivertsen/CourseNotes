#

tar -xvf filename

the dash is optional

Links:
https://kernel.org/
https://www.linuxfromscratch.org/lfs/view/systemd/chapter10/kernel.html


modprobe - allows for the search of modules

make mrproper - cleans previous builds to allow for a rebuild

make -j
-j stands for jobs -j16 allows you to use all 16 cores to run jobs faster

SBU stands for standard build unit

Kernel is the bridge between your hardware and the user

Packages needed to work:
```sudo apt-get install build-essentials```
Allows you to get the bare minimum


```sudo apt-get install libncurses-dev flex bison openssl libssl-dev dkms libelf-dev libudev-dev libpci-dev libiberty-dev autoconf```
Should be run to get all/rest