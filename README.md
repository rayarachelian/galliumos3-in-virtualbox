#**galliumos3-in-virtualbox**#

So I use Gallium OS 3 on a 2018 Acer Chromebook R11 which is serving me pretty well as a lightweight laptop and Android replacement. Price wise these can be had for ~$250 and have a nice 11" touch screen. A high end Samsung tablet or Apple iPad costs a lot more and does a lot less in my opinion.

While I do want to experiment and compile stuff on it, I don't want to wear out the built in eMMC compiling various code over and over, so I've attempted to get it working in VirtualBox and then transferring it over.

But for some reason the GalliumOS devs don't support it, and it's painful to get working. This is weird, since it would be easier to experiment in a VM than on real hardware.

So after much experimenting I got my vbox config working and would like to share it with you incase you have the same issues/goals.

The biggest pain in the ass is that it doesn't support ethernet out of the box in a plug and play matter like it does WiFi on real hardware.

You'll have run the ethernet.sh script to enable the controller. Once you do that, it will start to work. You may need to type in ethernet.sh manually, but it's a short file that just does ifconfig up and dhclient. There's probably easier ways of implementing this, but it's good enough for my needs for now.

You should edit the paths inside the .vbox file to make it work with your system, for example the paths to the install CD, etc.

I've also installed sshd on the VM so I can use sshfs from the host OS, as well as the usual stuff like linux kernel headers, gcc, etc. which are needed for the VirtualBox drivers to compile.

    sudo apt-get install linux-headers-generic gcc \
            openssh-server libfltk1.3 libfltk-images1.3 \
            
    There's still some issues in getting the vbox-greeter to come up since it can't connect to lightdm (instead of lxdm)
    But after this, the VBoxAdditions for linux install and I can change the display resolution.
    
    Sadly ethernet.sh has to be executed on each boot up.
    
