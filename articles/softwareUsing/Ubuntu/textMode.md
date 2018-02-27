# Ubuntu 16.04 boot into text mode

## Modify grub parameter

* Comment the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet"**

* Change **GRUB_CMDLINE_LINUX=”" to GRUB_CMDLINE_LINUX="text"**

* Uncomment this line **#GRUB_TERMINAL=console**

* bash: **sudo update-grub**

## Set run level

bash **sudo systemctl set-default multi-user.target** 