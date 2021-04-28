---
layout: post
title: "♪ Let's Get Virtual! ♪"
subtitle: '3 key tools for remote development.'
tags: [VM, How-To, Virtualization]
featured_image: assets/images/posts/2021/virtual.png
featured: true
hidden: false
---

At the time of this writing, social distancing and isolation are the perhaps the most recommended ways to "stay safe in these unprecedented times". It turns out that an isolated environment can keep your computer safe, too. Sandbox environments, virtual machines, and software containers can all help to protect your local machine from contamination or compatibility issues. Virtualization also increases flexbility, allowing you to run different OS-specific programs on the same hardware. And since the last year has proven that the only constant is change, virtual machines give the comfort of disaster recovery, making it easier to backup data or scale a platform. Regardless of the reason that your code isn't running locally, it's important that development feels seamless, with all the comforts of home.

## VirtualBox
This is not so much a tool as the real deal.

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
 ssh -p 2522 VM_USERNAME@127.0.0.1
 ```
11. If prompted about the authenticity of the host, enter yes.
12. Enter the password for your virtual machine, then you're in.


## Visual Studio Code Remote Development