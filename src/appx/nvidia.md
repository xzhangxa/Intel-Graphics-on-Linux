# Appendix A - NVIDIA Driver in Linux Graphics Stack

## A.1 - NVIDIA and Linux Open Source Community

NVIDIA is well known for not playing well with open source community, the company does not have much interest in support open source framework, and instead often only provided proprietary drivers and software for their hardware products. For Linux kernel driver NVIDIA only provided proprietary non-GPL drivers for years, and it was very common for latest NVIDIA proprietary kernel drivers lagged behind several releases of Linux kernel for fixed GCC compiler version, compilation errors with kernel headers etc. For other graphics software NVIDIA's stand is the same, they prefer to release their own proprietary software instead of support alternative open source software like Intel and sometimes AMD does.

So nouveau project was started in 2007 by developers who were frustrated by Nvidia's proprietary driver and lack of support to open source graphics stack. The project stared from reverse engineering and still is for now. NVIDIA did not directly support this project, however they did made agreement with nouveau developers to provide some helps of signed firmware, because starting from Maxwell 2 architecture only signed firmware were allowed. Also because of the signed firmware, there are too many problems that are only possible to be fixed by NVIDIA instead of nouveau developers. The nouveau driver, both as kernel DRM driver and a Mesa nouveau driver, has made upstream and is working for basic functionality, but also its feature support is always "in various states of disrepair". The user cannot expect too much from it except providing the basic display runtime support.

The [NVIDIA and nouveau](https://lwn.net/Articles/910343/) is a LWN article in 2022 to summarize the nouveau project till that time and some issues it was facing.

Because of the lack of interest to support Linux platform and proprietary only, non-GPL, few contributions to open source community, NVIDIA cards driver support for a Linux desktop machine is always the pain to experience. Also because of NVIDIA business style for their partners, NVIDIA received a lot of criticisms during the years. The most famous reflection of this in Linux community probably is [Linus Torvalds says “f–k you” to NVIDIA](https://arstechnica.com/information-technology/2012/06/linus-torvalds-says-f-k-you-to-nvidia/), [video](https://www.youtube.com/watch?v=_36yNWw_07g).

## A.2 - Official Open-Source Kernel Drivers

[NVIDIA Transitions Fully Towards Open-Source GPU Kernel Modules](https://developer.nvidia.com/blog/nvidia-transitions-fully-towards-open-source-gpu-kernel-modules/)

NVIDIA released their Linux driver of release R515 in 2022 in both proprietary and open source versions, and announced the NVIDIA Linux driver will be in a transition to open source kernel module in the future. After two years, the open source version is strong enough that it will be the default over the proprietary one and will be the only choice for future generations of NVIDIA GPU. The move is made because the secret part of the code is moved into GPU firmware now so the kernel driver can be GPL/MIT license and open sourced, and it can benefit the integration of the driver into Linux system.

- Keep using proprietary driver: Maxwell, Pascal, Volta
- Recommend to switch to open source kernel module: Turing, Ampere, Ada Lovelace, Hopper
- Must use open source kernel module: Grace Hopper, Blackwell