# How to set up a VirtualBox lab to debug Kernel Driver with Windbg

We consider here that on Computer A `windbg` is already installed and on Computer B Visual Studio, the SDK and WDK are installed.

![lab](https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/windbglab.png)

1) Open the `Host network Manager` to create or set up a new `Virtual Box Host-Only Ethernet adapter`

<p align="center">
<img src="https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/00.png" width="30%" height="30%">  
</p>

2) Create or choose a `Virtual Box Host-Only Ethernet adapter` and tick the `Enable` box for `DHCP Server`

<p align="center">
<img src="https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/01.png" width="60%" height="60%">  
</p>

3) For Computer A and Computer B go to `Settings -> Network` and in `Attached to` select `Host-Only Adapter` and then select the adapter previously set up or created. For us it's `VirtualBox Host-Only Ethernet Adapter`. Don't forget to tick the boxes `Enable Network Adapter` and `Cable Connected`

<p align="center">
<img src="https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/02.png" width="60%" height="60%">  
</p>

4) Retrieve on Computer A the IP with the `ipconfig` command

<p align="center">
<img src="https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/03.png" >  
</p>


5) Disable the firewall on both VMs

<p align="center">
<img src="https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/04.png" width="70%" height="70%">  
</p>


6) On computer B enable kernel debugging, setup the connection to Computer A for debug and enable test signing. 

For the command `bcdedit /dbgsettings`, for `hostip` set the IP of your Computer A, for `port` choose the one you want between 50000 and 50039. 

**The `bcdedit /dbgsettings` will output a Key, *KEEP IT* it will be used on the windbg configuration on Computer A to establish the connection !**


<p align="center">
<img src="https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/05.png" >  
</p>


7) On computer A, open Windbg, select `Attach to Kernel` and set the port you choose on Computer B and the key provided by the command `bcdedit /dbgsettings`.


<p align="center">
<img src="https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/07.png" width="70%" height="70%" >  
</p>


8) Now reboot Computer B. On Computer A you will see in the command prompt of windbg some data meaning that the connection is up.

<p align="center">
<img src="https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/08.png" width="70%" height="70%" >  
</p>


9) You can check by clicking on the button `Break`. If it work the VM should be freezed and you should see a `nt!DbgBreakPointWithStatus` message in the command windows of windbg

<p align="center">
<img src="https://raw.githubusercontent.com/xalicex/kernel-debug-lab-for-virtual-box/main/09.png" width="70%" height="70%" >  
</p>


