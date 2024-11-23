# Linux DRM Driver: i915 and Xe

## Switch from i915 to Xe

Intel started the Linux i915 driver for the integrated GPU since the i915 chipset at the generation of Gen3 (see [History](./history.md)). The future generations were supported in i915 driver with the name unchanged, after twenty years, i915 is still the default Intel GPU Linux driver for both iGPU and dGPU.

With the major change of discrete GPU business and Xe architecture, a new Linux DRM driver is introduced with the name Xe. The Xe driver is a fresh start without all the legacy functionality of i915 included for the old generations, and makes some major changes to better work with the latest Linux graphics stack and the new and later Xe architecture generations. The Xe DRM driver was merged to mainline Linux at v6.8, it will co-exist with i915 and replace it in the future for later Xe generations.

The major differences and improvements of Xe driver to i915 are:

- A
- B
- C
- D

## Source Code



## i915 Driver parameters
