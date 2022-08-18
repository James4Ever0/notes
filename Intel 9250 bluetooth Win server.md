---
tags: [alienware, bluetooth, driver, intel, linux]
title: Intel 9250 bluetooth Win server
created: '2022-03-23T16:41:23.000Z'
modified: '2022-08-18T15:31:56.454Z'
---

# Intel 9250 bluetooth Win server

intel driver & support assistant
https://www.intel.com/content/www/us/en/support/detect.html

unzip the it admin pack for win 10
https://www.intel.com/content/www/us/en/download/16807/intel-wireless-bluetooth-for-it-administrators.html

follow instructions to find and modify driver
https://www.sevenforums.com/network-sharing/415513-intel-wifi-ac-9260-driver-fir-win7-x32-x64.html
Intel has updated the drivers since my first post. Current is now 20.70

Download Intel(R) PROSet/Wireless Software and Drivers for IT Admins

You should be downloading WiFi_20.70.0_Driver64_Win7 (your first post mentions both x32 and x64 so I am not sure which one you are running. Hopefully x64) In the package is a Netwsw04.INF file but not a Netwsw03.INF file.

Something I did not think of until now, is we need to ALSO use the WIN10 download package in order to see the lines where Intel calls out your specific driver. To find that, you need to also download the WiFi_20.70.0_Driver64_Win10 package. Within it, we need to look at the Netwtw06.INF file which is the file that has your device. You will need to cut-n-paste the two lines within that file that contain the string PCI\VEN_8086&DEV_A370&SUBSYS_42A48086. Or better yet forget all that, I'll just cut-n-paste them now and include them in screenshots. You can ignore the Win10 download altogether in order to keep things straight.

So we cut and paste those two lines and put them within the Netwsw04.INF file that is in the win7 package. The first one goes at the top of the excludefrom select part, and the next one goes at the top of the DEVICE WIN7_64 section. I will attach a screenshots now of what these new lines look like within my editor. They are the highlighted lines. Since you cannot cut and paste from an image, here is the text of the two lines:

1st line

; PCI\VEN_8086&DEV_A370&SUBSYS_42A48086 , \

2nd line

%NIC_9462AC_HMC% = Install_MPCIEX_DELLM2CRF3DIVERSITY_9462_AC_HMC_WINT_64_AC , PCI\VEN_8086&DEV_A370&SUBSYS_42A48086 ; AC

As I mentioned before, the first line is near the top of the Netwsw04.inf file and the second line is about 5 pages down.

Here's a caveat, a new piece of information that is a potential show-stopper. See where within the second line there are three places where it says "AC"? That appears related to how the setup file integrates the driver later on in the file. Well over in the Win10 package it does not actually say "AC", instead it says "No_160", which is something that is part of the win10 package but not part of the win7 package. Based on text within the win10 setup file (the one named Netwsw06.inf) there appears to be a special section specifically for Dell machines called No_160. I'm over my head as to what exactly it all means, other than to say that since there is no section in the Win7 package called No_160, I had to change No_160 to AC in order for the win7 file to process the line, and of course it is possible that this driver cannot install without the No_160 section, meaning it is not installable on win7. So what that all adds up to is that when I first replied to you I was giving this method about a 70% chance of working, but now I would put the odds at 30%.
