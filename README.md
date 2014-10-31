360-wifi-linux
==============

Setting up [360 Mobile WIFI] (http://wifi.360.cn/) on Linux

(1) It has been tested on ubuntu 12.04 (kernel version < 3.4.0).

(2) Linux has a bug of USB 3.0 driver (dmesg | grep "ERROR no room on ep ring"). If it does not work on USB 3.0 slots, you can try the following workaround:

    a. Insert an old USB device (USB 2.0) into the USB slot and then remove it

    b. Insert 360 Mobile WIFI into the slot

    c. Run the script

(3) This script does *not* work for the second version of the 360 wifi

Installing the patched kernel driver
====================================

> sudo apt-get install --reinstall linux-headers-generic build-essential
> cd DPO_MT7601U_LinuxSTA_3.0.0.4_20130913
> make  
> su -c 'mkdir -p /etc/Wireless/RT2870STA/'  
> su -c 'cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat'  

Connect the USB

> su -c '/sbin/insmod os/linux/mt7601Usta.ko'

If works:

> su -c 'make install'