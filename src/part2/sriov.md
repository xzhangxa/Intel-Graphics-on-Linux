# SR-IOV Support

SR-IOV support on Intel GPU requires a few setups and relatively new software releases. These links may help:

- [vGPU (SR-IOV) with Intel 12th Gen iGPU [Updated Nov 2023]](https://www.michaelstinkerings.org/gpu-virtualization-with-intel-12th-gen-igpu-uhd-730/)
- [Intel Gen 12 vGPU (SR-IOV) on Proxmox](https://github.com/Upinel/PVE-Intel-vGPU)
- [Intel® Graphics SR-IOV Enablement Toolkit](https://www.intel.com/content/www/us/en/developer/articles/reference-implementation/graphics-sr-iov-enablement-toolkit.html)

Before supporting SR-IOV for virtualization, Intel has **Intel GVT-g** virtualization solution for Intel Gen8 and Gen9 iGPU from Boardwell (5th gen) to Comet Lake (10th gen). See [Intel GVT-g Setup Guide](https://github.com/intel/gvt-linux/wiki/GVTg_Setup_Guide)
