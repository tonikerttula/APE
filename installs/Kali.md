# Installing Kali Linux 2021.3 in VirtualBox 6.1.28 for Windows 10

This guide is for Windows 10 users.

Start by downloading VirtualBox, if you haven't yet. I downloaded Version 6.1.28 from [here](https://www.virtualbox.org/wiki/Downloads).

After you have downloaded VirtualBox, download the Kali Linux Virtual Machine 64-bit version for VirtualBox from [here](https://www.kali.org/get-kali/#kali-virtual-machines). The version number for my Kali is 2021.3.

#### Open VirtualBox, and navigate to File and Import Appliance.

![1]

#### Choose the downloaded Kali Linux file and click Next.

![2]

#### Next phase, choose a folder where you want to store the Virtual Machine, and click Import.

![3]

#### For the Software License Agreement Pop-up, click Agree.

#### The importing process will take a few minutes. 

#### Next, start the Virtual Machine by clicking Start in the Virtual Box Manager. The start up will take a few seconds, wait until you get the graphical login window.

(if you get the following error message, see the bottom of the page for solution)

![7]

#### If you don't get the error message, see the login credentials below!

![4]

### Login: kali
### Password: kali

The default keyboard layout might not be to your liking, you can change it by opening the Terminal emulator and typing in command "setxkbmap" and adding a country code for your wanted keyboard layout. I want finnish keyboard layout, so the command I used is:
> setxkbmap fi

![5]

Now try opening the browser, and typing in some URL. If you manage to get to the site, that means that your internet connection, keyboard and mouse all work! Congratulations, you have functioning Virtual Machine to use!

## Solving problems

### 1
If your internet access doesn't work, check if your Virtual Machine is attached correctly. Go to you Virtual Box Manager, select your Virtual Machine and click Settings. In the Network tab, see if your network adapter is set to NAT. If it isn't set it to NAT.

![6]

### 2

![7]

If you get the following error message when you start up your Virtual Machine, you need to check if you processor supports hardware virtualization. Open your task manager by pressing Ctrl+Shift+Esc, and going to the performance tab. In the bottom right you'll see if it says "Enabled" on the virtualization. My task manager is in finnish, but you'll see the location of the information regardless. If it says it isn't enabled, tough luck, I don't have the troubleshooting required here.

![8]

After you check that you have virtualization enabled, you'll need to reboot your computer and open the BIOS menu. Usually the key for Windows users is F2, so after you reboot your computer start mashing F2 until your BIOS menu opens.

In the BIOS menu, you will need to find the section for configuring your CPU. It should be called something like "CPU configuration" and may be behind "Advanced" or "Advanced Mode" selections.

After finding the CPU configuration section, you need to find the menu or option where it allows you to enable hardware virtualization. Hardware virtualization is enabled in the acceleration section. Depending upon your PC, look for any of these or similar names such as Hyber-V, Vanderpool, SVM, AMD-V, Intel Virtualization Technology or VT-X. After reaching the hardware virtualization menu, you'll need to select "Enabled" option for  If you see the options of AMD IOMMU or Intel VT-d, enable them as well. After all that is done, click save changes and exit the BIOS. The computer will restart with hardware virtualization enabled.

I had this same problem the first time I tried installing virtual machines for a new PC. I troubleshooted the problem by following the guide [here](https://www.virtualmetric.com/blog/how-to-enable-hardware-virtualization), but the above guide is paraphased version of it so you won't need to open many different websites.



[1]: https://i.imgur.com/iHL4rgv.png
[2]: https://i.gyazo.com/47fb79c0e8357d2b06dc69528034354e.png
[3]: https://i.gyazo.com/721c0a59e59eaad42b38520860c08580.png
[4]: https://i.gyazo.com/50613cdb9875851fdcba3f741d631136.png
[5]: https://i.gyazo.com/28f369b71c2680bef54f536e82d100a5.png
[6]: https://i.gyazo.com/67b1a0b81d068541f3dd0335c5a695d1.png
[7]: https://tonikerttula.files.wordpress.com/2021/10/image-12.png
[8]: https://i.imgur.com/zM64VzN.png
