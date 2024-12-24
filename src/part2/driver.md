# Linux DRM Driver: i915 and Xe

## Switch from i915 to Xe

Intel started the Linux i915 driver for the integrated GPU since the i915 chipset at the generation of Gen3 (see [History](./history.md)). The future generations were supported in i915 driver with the name unchanged, before the 2024 release of Lunar Lake with Xe2, i915 was always the default Intel GPU Linux driver for both iGPU and dGPU.

With the major change of discrete GPU business and Xe architecture, a new Linux DRM driver was introduced with the name [Xe](https://docs.kernel.org/next/gpu/rfc/xe.html). The Xe driver is a fresh start without all the legacy functionality of i915 included for the old generations, and makes some major changes to better work with the latest Linux graphics stack and the new and later Xe architecture generations. The Xe DRM driver was merged to mainline Linux at v6.8 and in the recently released LNL and Battlemage B580, only the Xe driver can be used.

Xe driver code-base also allows Intel to make use of more shared DRM/kernel infrastructure around TTM memory management, the DRM scheduler originally adapted from the AMDGPU driver, and other common elements. For areas like display handling, Intel's Xe driver is working to share code with the existing i915 driver where it has worked well and reduces the risk of hardware support regression, etc. In user-space, Intel's Iris Gallium3D driver and ANV Vulkan driver will work with this new kernel driver.


The major differences and improvements of Xe driver to i915 are:

- **Simplified Codebase**: i915 has a large and complex codebase that supports multiple generations of Intel GPUs. This complexity makes it difficult to add new features and maintain legacy functionality, small changes often take significantly longer and may affect unrelated areas. So Xe driver's No.1 and most important goal is "Simple as possible".
    - Xe removed tons of things modern UMDs do not need, uses much simpler uAPI that is easy to understand and fits 3D, Compute and Media UMDs needs.
    - Xe re-designed a simple and clear locking hierarchy whereas i915's is nearly incomprehensible;
    - Xe has clear layering and well-defined common structures, whereas i915 uses some common contexts everywhere(e.g., IRQ), and some layers are confusing and not fully correct(e.g., GuC submission and scheduling);
    - Xe provides clearer documentation for all common structures and large components.

- **Performance Optimization**: Xe driver integrated the dgfx foundation and DG2 support, and incorporated many datacenter features that were blocked by the multi-year refactoring effort needed for i915, such as:
  - SR-IOV: allows a single physical device to be shared among multiple virtual machines;
  - USM: Unified Shared Memory, allows the CPU and GPU to share the same physical memory to improve computational efficiency;
  - EUDebug: helping developers identify and resolve performance bottlenecks and errors;
  - long-running compute workloads: supporting efficient resource management and scheduling mechanisms for large-scale computational tasks;
  - ATS: Address Translation Services, allows devices (e.g., GPUs) to directly request and manage the translation of virtual addresses to physical addresses without going through the host CPU; etc.

- **Modern Architecture**:
  - i915 is architected for legacy UMD (e.g., OpenGL, X) and Xe is designed to meet the needs of modern graphics APIs(e.g., Vulkan and Level Zero).
  - i915 has poorly utilized shared DRM infrastructure and Linux upstream improvements. Xe uses the common DRM/DMA-BUF framework as much as possible, such as DRM scheduler for command submission and TTM for memory management.


## Source Code

[freedesktop kernel driver](https://gitlab.freedesktop.org/drm/)
- [i915 kernel driver](https://gitlab.freedesktop.org/drm/i915/kernel)
- [Xe kernel driver, branch: drm-xe-next](https://gitlab.freedesktop.org/drm/xe/kernel)

[Mainline Linux Kernel Archives](https://www.kernel.org/)
- [Mainline: 6.13-rc4, i915](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/drivers/gpu/drm/i915?h=v6.13-rc4)
- [Mainline: 6.13-rc4, Xe](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/drivers/gpu/drm/xe?h=v6.13-rc4)


## Further Reading

- [Xe](https://docs.kernel.org/next/gpu/rfc/xe.html)
- [DRM/i915 uAPI](https://www.kernel.org/doc/html/latest/gpu/driver-uapi.html#drm-i915-uapi)
- [DRM/Xe uAPI](https://www.kernel.org/doc/html/latest/gpu/driver-uapi.html#drm-xe-uapi)