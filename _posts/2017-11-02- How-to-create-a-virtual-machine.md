---
layout: post
title: How to create a Virtual machine
---

I remember an incident at work a few years ago, we needed a VM urgently, to test a web page on a different version of IE.
My colleague volunteered for creating this VM, and I thought then - "Wow, he knows how to do this, he's a guru!". 
Back then I was a newcomer at the company and previously I have never used VMs, let alone create one.

Now I understand that this is not a big deal, and everyone can do it by following a tutorial.


##### Why should one use VMs?

- for testing, in case you need to do cross-browser testing. It allows you to have different versions of browsers in addition to versions you use on your host OS.
- for trying a new OS. In case you want to switch to Linux for example, but have never used it before, it is a good idea to create a VM with Linux to see if it works for you.
- for the possibility to use the snapshots to roll back easily

##### Overview of this guide
By the time you're done with this tutorial, you will be able to: 
- create your own VM
- create VM snapshots
- use snapshots to restore the state of your VM

##### Terminology

- host - your real computer on which the VM runs.
- guest - your VM.
- snapshot - a copy of the state of the guest system that you can revert to at any point.


 


##### VirtualBox
1. [Download VirtualBox](https://www.virtualbox.org/wiki/Downloads) and install it. It is a free and open-source program.

![_config.yml]({{ site.baseurl }}/images/VM1.PNG)

2. Install VirtualBox extension pack, which extends the functionality of the VirtualBox; for example it provides the USB functionality.

3. Download the operating system you will install on your VM (in my case - [Ubuntu](https://www.ubuntu.com/download)).


4. Set up your VM

*Name and OS*
Open `VirtualBox` -> Click on `New` icon -> In the new window enter the `Name` of your VM (it can be anything, as long as it helps you remember what this VM is for later; this is especially relevant if you have multiple virtual machines)-> Select the `Type` of operating system you want to install on your VM (in the previous step we downloaded it).

![_config.yml]({{ site.baseurl }}/images/VM10.PNG)

*Memory*
Allocate the `RAM` for your `VM`. It will be used only when the VM is running, otherwise this memory is given back to your system. When choosing the amount of memory, consult the recommended requirements for your OS of choice.

![_config.yml]({{ site.baseurl }}/images/VM11.PNG)

*Hard disk file type*
Leave the default option `Create a virtual hard disk now`.

![_config.yml]({{ site.baseurl }}/images/VM12.PNG)

*Storage on physical hard disk*
Select `Dynamically allocated` for more flexible storage management. This means that initially the virtual disk will have a small size and it will expand once something is written to it (up to the allocated space). Otherwise, if you choose `Fixed storage`, the entire space will be allocated right away and taken from your host (i.e. real computer), even if the VM doesn't use it yet.  

I selected the `Dynamically allocated` option.

![_config.yml]({{ site.baseurl }}/images/VM13.PNG)


*File location and size*

Choose the `location` you want your VM be stored in and the `size` of the `virtual hard drive`. Consult your guest OS recommended requirements when choosing the disk size.

![_config.yml]({{ site.baseurl }}/images/VM14.PNG)


##### Installing the guest OS

Open `VirtualBox` -> Select your `VM` -> Go to `Settings` -> Select `Storage` -> Add the virtual disk into the CDROM (you downloaded your OS previously)->  Click `Start` to power on the virtual machine.

![_config.yml]({{ site.baseurl }}/images/VM16.PNG)

![_config.yml]({{ site.baseurl }}/images/VM17.PNG)

Click on `Install Ubuntu` -> Check the `Download updates while installing Ubuntu` checkbox -> Click on the `Continue` button ->  Check the 'Erase disk and install `Ubuntu` radiobutton -> Click `Continue`.

![_config.yml]({{ site.baseurl }}/images/VM18.PNG)

![_config.yml]({{ site.baseurl }}/images/VM19.PNG)

![_config.yml]({{ site.baseurl }}/images/VM20.PNG)

![_config.yml]({{ site.baseurl }}/images/VM21.PNG)


Follow the steps of the installation wizard, you can leave the default values unchanged or adjust them as you see fit. These details are beyond the scope of the tutorial.

![_config.yml]({{ site.baseurl }}/images/VM22.PNG)



##### Snapshots 

A snapshot allows you to save the current state of your machine and restore it to that state later. You can make some experiments on your machine, without worrying that you can break anything, because you can always restore it in a few clicks. 

If you would like to take a snapshot you can do it by clicking the `Machine` tab -> Select `Take Snapshot` -> Enter the snapshot `Name` -> Enter the `Snapshot Description`.


To restore the state you saved in a snapshot you need to open VirtualBox -> In the right frame of the window you will see the list of your snapshots -> Right-click the one you need and select `Restore`. Now your VM is restored to the point the snapshot was created.



##### Conclusions
This is basically the procedure of creating a virtual machine.

It is a really cool and useful thing. As a tester, I use them intensely in some projects, running the software on different platforms using a single computer.















































 

