# Project log in Zynq-7010

## ***Hello World***

### 05/05/2018

- ***Source Compiling failed***

**Details**: arm-none-eabi-gcc: No such file or directory

**Solutions**: This problem is due to **32-bit lib** missing. So, we install some **32-bit lib** in Ubuntu 16.04.
[reference](https://www.xilinx.com/support/answers/63561.html)

```shell
sudo dpkg --add-architecture i386
sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0 lib32stdc++6
```


- ***Serial Port NOT found***

**Details**: When connecting the **SDK_console** with the Board, it didn't show any available serial USB port.

**Solutions**: In Ubuntu16.04, when Zybo is connected to the PC, there will be a **ttyUSB** in /dev. What we need do is add currently user to the group which **ttyUSB** belongs to(**dialout**). 
[reference](https://reference.digilentinc.com/vivado/installing-vivado/start)

```shell
sudo adduser $USER dialout
```

### 05/07/2018

- ***Updating linux kernel failed***

**Details**: After updating linux kernel, Nvidia driver cannot work. So, I tried to update Nvidia driver. **But**, after a series of operations, linux kernel wasn't correctly built on the new Nvidia kernels. Many bins, like ***reboot***, ***shutdown*** were missing.

**Solutions**: Reload a Linux System. Before that, some files are to be backed. 

- /home/.bashrc
- /opt/
- /etc/

### 05/08/2018

- ***"Hello World" cannot be displayed via UART serial port***

**Details**: When connect a serial port (/dev/ttyUSB1) to a SDK terminal and run the **hello_world** program, SDK terminal shows nothing. That is to say: data transmission through UART serial port fails. 


**Solutions**: I followed the user guide which targets ZC702 board, not Zybo board. So, when I found the user guide targets Zybo, I found I choose the wrong board at the beginning of the project. I should choose **Zybo**, not **Zybo Z7-10**. After changing the board, "hello world" finally can be displayed in the SDK terminal. 
[reference](https://reference.digilentinc.com/learn/programmable-logic/tutorials/zybo-getting-started-with-zynq-server/start)

## ***AXI CDMA(Central DMA)***

### 05/09/2018

- ***Implementation failed***

**Details**: Z-7010 doesn't have enough **LUT** resources to map the FPGA design, in which modules related to CDMA take up many LUT resources. So, this sample project cannot be done in Z-7010.

