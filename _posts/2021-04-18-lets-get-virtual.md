---
layout: post
title: "♪ Let's Get Virtual! ♪"
subtitle: '3 key tools for remote development.'
tags: [VM, How-To, Virtualization]
featured_image: assets/images/posts/2021/virtual.png
featured: false
hidden: false
---

At the time of this writing, social distancing and isolation are the perhaps the most recommended ways to "stay safe in these unprecedented times". It turns out that an isolated environment can keep your computer safe, too. Sandbox environments, virtual machines, and software containers can all help to protect your local machine from contamination or compatibility issues. Virtualization also increases flexbility, allowing you to run different OS-specific programs on the same hardware. And since the last year has proven that the only constant is change, virtual machines give the comfort of disaster recovery, making it easier to backup data or scale a platform. Regardless of the reason that your code isn't running locally, it's important that development feels seamless, with all the comforts of home.

## VirtualBox
VirtualBox is a desktop application that allows your computer to run multiple operating systems without needing a dual-boot or any other software that might react poorly with your existing OS. It came in handy when I was developing an application that required Ubuntu, and I've used it often since then to test cross-platform compatibility and run code in an isolated environment. All you need to download is the VirtualBox application and the ISO file (or "image") of the new operating system.  
As an example, here's a guide to setting up a virtual machine with Ubuntu 18.04 on a Mac OS home environment:
1. Download and install [VirtualBox](https://www.virtualbox.org/).
2. Download the [Ubuntu 18.04 desktop image](https://releases.ubuntu.com/18.04.5/?_ga=2.146335351.2121979773.1620581367-542056388.1620581367). Take note of where the file is saved.
3. Open the VirtualBox application and add a new machine. If you start entering 'Ubuntu' as the name, it should autofill Linux and Ubuntu (64-bit) as the type and version, respectively.
4. Press continue (accepting the defaults) for memory size and hard disk.
5. Select VDI (Virtual Disk Image) as the hard disk type.
6. Select Dynamically allocated for the storage on physical hard disk.
7. Accept the default values for file location and size, then press Create.
8. In the VirtualBox Manager, select your newly created machine and press Start (Normal Start).
9. It should prompt you to select a virtual optical disk file. Click the folder icon to browse to the Ubuntu 18.04 ISO file saved in step 2.
10. In the install wizard, choose Install Ubuntu, select your desired keyboard layout, then select Normal installation.
11. Then it'll ask about the installation type. Select Erase disk and install Ubuntu. Spooky! But that's the beauty of virtualization; your home environment is completely protected.
 ![](/assets/images/posts/2021/lets-get-virtual/installation-type.png)
12. Press continue for the rest of the options. Enter a username and password when prompted, then restart the virtual machine.   

\
You now have a fully functional Ubuntu environment! Options such as RAM, storage size, and display ratio can be tweaked and configured to suit your needs (within the constraints of your hard drive).

## SSH
The ability to communicate between your local machine and the virtual one will come in handy time and time again. We also need SSH for the final, pinnacle step, so let's see how to set that up:
1. Start up the virtual machine you just created and log in.
2. Open the Terminal app in the virtual machine.
3. Install openssh-server by running the following commands:
    ```
    sudo apt-get update
    sudo apt-get install openssh-server
    ```
4. Power off the virtual machine.
5. In the VirtualBox Manager, select your new machine and click Settings.
6. Go to the tab for Network.
7. Under Adapter 1, open Advanced and click Port Forwarding.
8. Add the following entry:
 ![](/assets/images/posts/2021/lets-get-virtual/network-entry.png)
9. Start up the virtual machine.
10. From your local machine, open Terminal and enter the following command, replacing YOUR_USERNAME with the account you set up:
 ```
 ssh -p 2522 YOUR_USERNAME@127.0.0.1
 ```
11. If prompted about the authenticity of the host, enter yes.
12. Enter the password for your virtual machine, then you're in.


## Visual Studio Code Remote Development
This one is a *game changer*. Visual Studio Code is a free, open source code editor with all the extensions you could wish for. In particular, the [Remote Development Extension Pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack) allows you to edit code that's located in a container, virtual machine, or remote server, right from your local environment. This means that you can seamlessly swap between multiple environments without having to copy any source code to your computer.  
Setting it up is quick and simple for any environment to which you have SSH access. Let's see how to configure it for the virtual machine that we installed earlier:
1. In the VirtualBox Manager, start up the Ubuntu virtual machine. We don't need to interact with it directly, so you can minimize the window.
2. On your home machine, download and install [Visual Studio Code](https://code.visualstudio.com/). Open it, then download and activate the [Remote Development Extension Pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack).
3. On the left sidebar, you should now see the Remote Explorer pane. Open it, and in the dropdown at the top, select SSH Targets.
4. Click the plus icon to add a new SSH target. Enter the same SSH connection command that you used from the command line above: `ssh -p 2522 YOUR_USERNAME@127.0.0.1`
5. Select your SSH config file if prompted.
6. You should now see your virtual machine as an SSH target in the Remote Explorer. Hover over the name, then press the folder icon to Connect to Host in New Window.
7. Enter your password when prompted, then you have access to create and modify files as desired.

## ---
The capabilities of these three tools truly enrich the experience of virtualization and remote development. Not only do they give developers the freedom to test new versions with the safety net of isolation, they facilitate cohesion and consistency in team-based development, allowing all contributors to work in the same environment. By decoupling the technology from the available infrastructure, virtualization opens the door for improved efficiency, increased flexibility, and bolder innovation. And *that* seems like something worth dancing about.