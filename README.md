# Nougat TouchWiz kernel for a3xelte
## Warning: this is for Nougat stock and based on TouchWiz custom ROMs only
How to build this kernel?

1. Download this toolchain: `aarch64-cortex_a53-linux-gnueabi` here: https://www.androidfilehost.com/?fid=457095661767130542 and extract it
	- Example here: `/opt/toolchains/aarch64-cortex_a53-linux-gnueabi-GNU-6.3.0/`
	
- Edit `Makefile`
	- Search `CROSS_COMPILE` variable
	- Replace value by the bin prefix of toolchain
		- Like this: 
		`CROSS_COMPILE	?= /opt/toolchains/aarch64-cortex_a53-linux-gnueabi-GNU-6.3.0/bin/aarch64-cortex_a53-linux-gnueabi-` 
		(don't forget the "-" dash at end)
		
- Run `build_kernel.sh`

Outputs: 

You can find output in :
- Kernel : arch/arm64/boot/Image
	- To use it, rename it in Kernel-zImage in split_img folder of boot.img extracted
	
- module : drivers/*/built-in.o

How to clean?

Run this: `make mrproper`
Or: `make clean`
Or: `make ARCH=arm64 distclean`

_Tips_

- If you have a good config, you can allocate more memory to make process
	- Edit `build_kernel.sh`
	- Search for `-j5` parameter
	- Edit it to `-jN`, replace N by the number of thread of your PC (like 6, 8, more...)
