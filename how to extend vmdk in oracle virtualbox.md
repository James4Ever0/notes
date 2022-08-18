---
tags: [disk expansion, system manage, virtualbox, virtualization]
title: how to extend vmdk in oracle virtualbox
created: '2022-07-05T13:56:23.000Z'
modified: '2022-08-18T14:56:30.456Z'
---

# how to extend/resize vmdk in oracle virtualbox

win 7 扩容:
开始菜单 计算机 右键 管理 存储 磁盘管理

original article:
https://www.patricia-anong.com/blog/2017/11/1/extend-vmdk-on-virtualbox

When I first started using Oracle VirtualBox, I would mostly stick with the default options when creating a virtual machine. I soon realized, that wouldn't work for RDBMS installations, and although I would just add new virtual disk drives, I started to have unused or 100% full disks on some VMs. Rather than delete the VM, I decided to learn how to extend the existing disks, the steps are listed below:

Note: The Oracle Virtualbox Hypervisor is installed on a Windows OS

Open a command prompt:

Change directories to the VirtualBox Installation

cd C:\Program Files\oracle\VirtualBox

List the info on the disk you want to resize

VBoxManage showhdinfo “C:\Users\panong\VirtualBox VMs\CENTOS-6.7\D0.vmdk”

Run the command to resize:

VBoxManage modifyhd “C:\Users\panong\VirtualBox VMs\CENTOS-6.7\D0.vmdk” --resize 50000

6.png
If you receive the error below, then you will have to create a new disk, clone the data on the existing disk to the new disk and then delete the original disk:

7.png
Create a new VMDK “dynamic” disk

VBoxManage createhd –filename “C:\Users\panong\VirtualBox VMs\CENTOS-6.7\D11.vmdk” --size 50000

Clone old disk to the newly created disk
VBoxManage clonehd “C:\Users\panong\VirtualBox VMs\CENTOS-6.7\D0.vmdk” --existing “C:\Users\panong\VirtualBox VMs\CENTOS-6.7\D11.vmdk”


Release the old disk

Go to Virtualbox Media Manager ---> Select D0.vmdk ---> Click the "Release" option.

Note: DO NOT DELETE IT YET

Add the new disk to the Virtual Machine

Open the Machine folder and check the permission of the created hard disk. If it doesn't have the proper permission then it gives error while attaching to the machine

Open the Settings of the Virtual Machine ----> Storage ---> Add Hardisk -----> Select the hard disk that was just created.

Make sure to remove all disks, then add the new one first to be /dev/sda.

You're not done yet! If you start the VM now, the disk space will not be present since it has not yet been presented and allocated to your Linux Server.

To allocate the new disk, you will need to use GParted - a GUI for editing disk partitions.

To download GParted, go to http://gparted.sourceforge.net/livecd.php to download the ISO file named GParted Live CD (Be sure to get the current version based on the architecture of your OS e.g. 32-bit vs 64-bit). 

Create a new virtual machine for the GParted ISO on a Linux OS. Select Do not add a Hard Drive and ignore the warning.

Select the GParted VM, go to Settings -----> Storage -----> Controller: IDE Controller -----> Add a new CD/DVD. Add the GParted ISO file as the first item under Controller: IDE section and delete any additional empty disk slots. Add the disk that you wish to resize( C:\Users\panong\VirtualBox VMs\CENTOS-6.7\D11.vmdk) under the Controller: SATA Controller section -----> OK.

Start the GParted VM ----> GParted Live. Do not change any of the default settings. Press the power button on the GParted VM to start it.

Now, you should have made a backup of your vdi at this point. If you haven’t go back and do that – so many things can go wrong here and you are on your own!

If it is any partition other than /dev/sda1 you can right-click the partition you wish to resize and choose Resize/Move. 

IF YOU PREFER TO CREATE A NEW PARTITION WITH THE ADDITIONAL DISK SPACE YOU NEED TO CREATE A PARTITION:
Device —-> Create Partition Table

It should be back to main screen, click on New —-> Add (it should have selected all the free space - 20000MiB) —-> Add

You should see it now listed as New partition #1 not unallocated anymore.

Click on Apply at the top of the GUI, then confirm again by clicking Apply. Click Close. You should now see the disk listed as /dev/sda# with 20Gb.

Exit the GParted VM. 

Log on to the VM for the disk you just resized and everything should be functional and the /dev/sda drive should show the new size of 50Gb.

Delete the Original Disk Drive

Click the Remove option - this allows you to keep the HDD without deleting it from the system if you choose.
