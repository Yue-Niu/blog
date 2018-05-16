# Project log in Zynq-7010 runing os

## ***running os with SD card***

### 05/15/2018

- ***illegal instruction***

**Details**: when I load the os from SD card, mounting SD onto /mnt/, running a **hello world** program, it show **illegal instruction**. 

**Solutions**: The **hello world** elf file was compiled for arm cpu without a system. It doesn't targets os, and it consists many embedded xilinx lib initializing the arm cpu. So, I think maybe it's this reason that cause the **illegal instruction**. I tried to write a simple **hello world** program without Xilinx head file, and compile it using Xilinx compiler. It finally worked in the embedded OS.

- ***network configure failed***

**Details**: After I started the embedded os system, I tried to configure the local network by edit /etc/network/interfaces.
```shell
auto eth0
iface eth0 inet static
address 192.168.1.6
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
broadcast 192.168.1.255
```
then, I restart the **eth0**
```shell
ifdown eth0
ifup eth0
```

When I tries to ping the network using another host computer in the same local network (192.168.1.0), it fails.

**Solutions**:

## ***Custom IP and its driver***

- ***Cannot find ".h" file***

**Details**: When I use **petalinux-create -t apps --name blinkApp --enable** to create a new app, it only generate a default ".c" file. I have the ".h" to be added into. However, when I replace the ".c" file with mine, and add new ".h" file. It fails to pass the compilation, showing no such "blink.h" file.

**Solutions**: Actually, in the new petalinux version(2017.4), I need to add "blink.h" into the **blinkApp.b** file. So that, the compiler can find the header file.

- ***unlocked_ioctl: incompatible pointer type***

**Details**: When I compile the "blink.c" driver code, it shows a error message "incompatible pointer type for unlocked_ioctl". The related code is as follows:

```c
int device_ioctl(struct file *file, unsigned int ioctl_num, unsigned long ioctl_param){
	
}

struct file_operations Fops={
	.unlocked_ioctl = device_ioctl,
}
```

**Solutions**: After many searches, I found that actually in the new linux kernel, the return type for **unlocked_ioctl** changed from **int** to **long**. So, after I change the return type of **device_ioctl**, it pass compilation.