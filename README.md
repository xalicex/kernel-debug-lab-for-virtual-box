# kernel-debug-lab-for-virtual-box

We consider here that on Computer A `windbg` is already installed and on Computer B Visual Studio, the SDK and WDK are installed.

![lab](https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/windbglab.png)

1) Open the `Host network Manager` to create or set up a new `Virtual Box Host-Only Ethernet adapter`


![host network manager panel](https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/00.png)

2) Create or choose a `Virtual Box Host-Only Ethernet adapter` and tick the `Enable` box for `DHCP Server`

![Enable Virtual Box Host-Only Ethernet adapter](https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/01.png)

3) For Computer A and Computer B go to `Settings -> Network` and in `Attached to` select `Host-Only Adapter` and then select the adapter previously set up or created. For us it's `VirtualBox Host-Only Ethernet Adapter`. Don't forget to tick the boxes `Enable Network Adapter` and `Cable Connected`

![Setup network](https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/02.png)

4) Retrieve on Computer A the IP with the `ipconfig` command


![Setup network](https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/03.png)

5) Disable the firewall on both VMs

![Setup network](https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/04.png)

6) On computer B enable kernel debugging, setup the connection to Computer A for debug and enable test signing. 

For the command `bcdedit /dbgsettings`, for `hostip` set the IP of your Computer A, for `port` choose the one you want between 50000 and 50039. 

**The `bcdedit /dbgsettings` will output a Key, *KEEP IT* it will be used on the windbg configuration on Computer A to establish the connection !**

![Enable Debug on computer B](https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/05.png)
