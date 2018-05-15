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