# 1 - Introduction

This document is a summary of the Linux graphics stack and Intel GPU.

The Linux graphics software stack includes many individual and connected components, from kernel space to user space, from past to the current and future. This document focuses on the current general setup as the middle of year 2024. Not all components will be documented, however the whole picture and the most important concepts as the writers understand shall be provided to the readers to know how Linux works with GPU in general and could use this document as a reference to GPU under Linux in the daily use of Linux machines and development.

For Intel GPU, this document aims to be a summary of information. General knowledge of Intel GPU and its software will be documented for the average developers to understand the background, history and capabilities; More information for developments shall be mentioned and referenced to so when needed the developers can find the details themselves.

The target audiences of this document are interested developers, the prior knowledge of Linux graphics stack and Intel GPU are not needed.

# Part 1 - Linux Graphics Stack

[xin]

# 2 - Linux Graphics Stack Overview

## 2.1 - Overview

## 2.2 - Terminology

# 3 - Linux Kernel

## 3.1 - Linux DRM subsystem

TTM, GEM, DRI
A section or a paragraph for direct console output? 
drm-lease

[xin]

# 4 - User Mode Driver and Desktop

## 4.1 - X Window: Legacy and History of 40 Years

[xin]

## 4.2 - Wayland: A Linux Graphics "Future" Since 10 Years Ago

[xin]

### 4.2.1 - Compositor

### 4.2.2 - Issues

## 4.3 - Mesa

[wenke]

## 4.4 - Desktop Environment

[xin]

# 5 - Graphics API and Gaming Engine

[wenke]

# 6 - Pipeline from Application to Screen

[hongda]

# Part 2 - Intel GPU

# 7 - History, Present and Future

[kaili, xin]

# 8 - Internal

3D, Media, Display, Compute

# 9 - Drivers

# 10 - Firmware

# 11 - Media

# 12 - Compute

# Appendix A - Nvidia

## A.1 - Nouveau, and "So Nvidia, Fuck You"

Nouveau 是一个法语单词，意思是“新”。这个名字反映了它作为一个新生的开源驱动程序的身份。Nouveau 项目由一群热情的开发者发起，他们希望为 Nvidia 显卡提供一个自由、开源的替代方案。这个项目的起源可以追溯到 2005 年，当时一些开发者对 Nvidia 的闭源驱动程序感到不满，决定自己动手开发一个开源版本。

Nouveau 的开发过程充满了挑战，因为 Nvidia 并没有公开他们硬件的详细文档。开发者们不得不通过**逆向工程**来理解 Nvidia 显卡的工作原理。这就像是试图解开一个复杂的谜题，他们需要仔细观察显卡的行为，猜测其内部机制，然后编写代码来模拟这些行为。

尽管面临诸多困难，Nouveau 仍然取得了显著的进展。它现在已经成为 Linux 内核的一部分，为许多 Nvidia 显卡提供了基本的支持。虽然在性能和功能上可能不如 Nvidia 的专有驱动程序，但它的存在对于开源社区来说具有重要意义。

<img src="./Fuck you Nvidia.png" width = "200" height = "250" alt=" " align=center />

"So Nvidia, Fuck You" 这个短语源自 Linus Torvalds 的一次著名事件。Linus 是 Linux 内核的创始人，以直言不讳和幽默感著称。在 2012 年的一次公开演讲中，有人问他对 Nvidia 在 Linux 平台上的支持有何看法。Linus 对 Nvidia 的闭源策略和缺乏合作感到非常不满，于是他竖起中指，说出了*So Nvidia, Fuck You*这句话。

这一事件迅速在互联网上传播开来，成为了一个经典的开源社区故事。Linus 的这一举动不仅表达了他个人的愤怒，也反映了许多开源爱好者对 Nvidia 的不满。这一事件还激励了更多人参与到开源驱动程序的开发中，进一步推动了 Nouveau 项目的发展。

## A.2 - Official Proprietary and Open-Source Drivers

<img src="./Nvidia drivers.png" width = "650" height = "400" alt=" " align=center />

[NVIDIA Transitions Fully Towards Open-Source GPU Kernel Modules](https://developer.nvidia.com/blog/nvidia-transitions-fully-towards-open-source-gpu-kernel-modules/)

NVIDIA在2022年5月发布了R515驱动程序，首次将Linux GPU内核模块以开源形式发布，并计划在即将到来的R560驱动更新中完全过渡到开源模块。这些开源驱动程序提供了改进的性能和新功能，如异构内存管理和保密计算，但并不是所有GPU都兼容这些开源模块。NVIDIA建议新一代GPU架构用户切换到开源模块，而旧架构用户则应继续使用专有驱动程序。


| 架构名称      |                                  |
| ------------ | ---------------------------------|
| Maxwell      | 继续使用 NVIDIA 专有驱动程序       |
| Pascal       |                                  |
| Volta        |                                  |
| Turing       | 建议切换到开源 GPU 内核模块        |
| Ampere       |                                  |
| Hopper       |                                  |
| Ada Lovelace |                                  |
| Grace Hopper | 必须使用开源 GPU 内核模块          |
| Blackwell    |                                  |