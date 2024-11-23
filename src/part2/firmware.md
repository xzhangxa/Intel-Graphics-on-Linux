# Intel GPU Firmware

- GuC: Graphics micro (μ) Controller, starting from Gen9. Scheduling, context submission, and power management.
- HuC: HEVC/H.265 micro (µ) Controller, starting from Gen9. Offloading some media decoding functionality from CPU.
- DMC: Display Micro Controller, starting from Gen9. DMC in display engine to save and restore the state of display engine when it enter into low-power state and comes back to normal.
- GSC: Graphics System Controller, starting from Meteor Lake.

These firmware blobs can be found in Linux distributions' *linux-firmware* package. To download them directly, see [intel-gpu-firmware](https://github.com/intel-gpu/intel-gpu-firmware) and [igsc](https://github.com/intel/igsc).