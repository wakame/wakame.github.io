---
layout: page
title: Demo Image
header: Virtualbox Demo Image
group: navigation
---
{% include JB/setup %}

This is a [VirtualBox](https://www.virtualbox.org/) image that contains Centos 6.4 with Wakame-vdc peinstalled. This is intended for people to get a first introduction to Wakame-vdc with a minimal amount of configuring required.

[Download the Wakame-vdc demo image.](http://dlc.wakame.axsh.jp/demo/1box/vmdk/1box-lxc.netfilter.x86_64.vmdk.20130709.zip)

## Requirements

Any computer with an x86_64 processor capable of running VirtualBox.

## Setup

Download and unzip the image.

In VirtualBox, click *File* and select *Preferences*.

![Select file/preferences.](vbox_screenshots/01_File_Preferences.png)

Click on Network and create a new host-only network.

![Click *network*, then click *add host-only network (Ins)*.](vbox_screenshots/02_Settings_new.png)

Now click on the screwdriver icon for host-only network settings.

![Click the screwdriver icon](vbox_screenshots/03_settings_screwdriver.png)

Set the IPv4 subnet to 10.0.2.2/24. Leave IPv6 fields blank.

![IPv4 Address: 10.0.2.2. IPv4 Network Mask: 255.255.255.0.](vbox_screenshots/04_host_onlysettings.png)

Disable the host-only network's DHCP server.

![Click the DHCP Server tab and uncheck *Enable Server*.](vbox_screenshots/05_dhcp_settings.png)

You're done with VirtualBox preferences. Now create a new virtual machine.

![Exit the preferences dialog and click *New*.](vbox_screenshots/06_new.png)

Set the following settings for name and operating system.

![Name: Wakame-vdc 1box, Type: Linux, Version: Red Hat (64 bit)](vbox_screenshots/07_name_os.png)

Set the memory size for the VM. 3GB recommended. 1GB minimal.

![3072 recommended. 1024 minimal.](vbox_screenshots/08_memory.png)

Select *Use an existing virtual hard drive file* and browse to the Wakame-vdc demo image that you have downloaded.

![Select the Wakame-vdc demo image as the virtual hard drive file.](vbox_screenshots/09_hd.png)

You've now set up VirtualBox VM but you still need to do some extra network settings before Wakame-vdc will work right.

![Click *settings* in the main VirtualBox window.](vbox_screenshots/10_settings.png)

Click *Network* and enable *Adapter 1*. Attach it to the *Host-only Adapter* that you have created above. Make sure to set *Promiscuous Mode* to *Allow All*. This will allow us to make network connections to Wakame-vdc instances.

![Attached to: *Host-only Adapter*, Name: *vboxnet0*, Promiscuous Mode: *Allow All*, Cable connected: *true*](vbox_screenshots/11_host_only.png)

Also enable *Adapter 2* and attach it to an *Internal Network*.

![Attached to: *Internal Network*, Name: *intnet*, Promiscuous Mode: *Allow All*, Cable connected: *true*](vbox_screenshots/12_internal.png)

You're done. Start the Wakame-vdc demo image.

![Click *start* in the main VirtualBox window.](vbox_screenshots/13_start.png)

On first boot, the image will take some time to set up several Wakame-vdc services like the MySQL databases.