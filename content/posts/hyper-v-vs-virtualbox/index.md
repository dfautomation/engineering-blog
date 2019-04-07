---
title: "Windows Hyper-V vs Oracle VM VirtualBox"
date: 2019-04-07T17:11:08+08:00
author: "Patrick Chin"
tags: ["virtualization"]
---

To run virtualization task on Windows, two of popular hypervisors that come to mind are Windows Hyper-V and Oracle VM VirtualBox. One of the problem is you cannot run both hypervisors software at the same time, and you cannot switch between them without a system reboot. [^1]

As users of both of these software, we have came out a list of pros and cons for Hyper-V and VirtualBox, so you can decide which hypervisor you would use.

Pros of Hyper-V
---

- Checkpoints can be created fast and efficiently.

  - We use this a lot to revert our VMs to a previously saved state, when we are experimenting with something.

- It supports the differencing disk format which allows multiple VMs to share a base disk image.

  - You could save some hard disk space here when you run multiple copies of the same instance, or when your instances share the base image of an OS.

- It can automatically save your VM state during host shutdown, and restore the VM when the host boots up.

- "Docker for Windows" runs on Hyper-V (note that the older "Docker Toolbox" still run on VirtualBox though)

  - If you might want to run Docker, you should probably go for Hyper-V.

Cons of Hyper-V
---

- It is not available in some editions of Windows, such as Window 10 Home Edition.
- Limited and difficult networking configurations.

  - Try configure NAT port forwarding for the internal network in Hyper-V ! [^2]

Pros of VirtualBox
---

- It can fallback to software virtualization if your CPU does not support hardware virtualization natively.
- It has better emulation of your hardware including graphics, audio, and USB.
- VirtualBox Guest Additions make things wonderful (when it is being installed in the guest VM).

  - Host OS folders can be directly mount inside the guest VM.
  - Screen resolution of the guest VM is adjustable on-the-fly just by resizing VM window.

- It supports many virtual disk formats, including VDI, VMDK and VHD whereas Hyper-V only supports its own VHD format.
- It has more networking options for the VMs.

Cons of VirtualBox
---

- VirtualBox might have a slightly slower performance than Hyper-V.


Both Hyper-V and VirtualBox are excellent software for virtualization, and there is no clear winner here. Happy choosing your own hypervisor!


[^1]: https://www.hanselman.com/blog/SwitchEasilyBetweenVirtualBoxAndHyperVWithABCDEditBootEntryInWindows81.aspx
[^2]: https://www.thomasmaurer.ch/2016/05/set-up-a-hyper-v-virtual-switch-using-a-nat-network/
