# Fairphone 6 kernel prebuilts

The DiamaneOS kernel, modules and device tree for the Fairphone 6, built from
source with `diamaneos kernel build`. The Android build reads them from
`device/fairphone/FP6-kernel`.

## This build

- Sources: [kernel_qcom-6.18](https://github.com/DiamaneOS/kernel_qcom-6.18) at `4c90b85` and [kernel_common-6.18](https://github.com/DiamaneOS/kernel_common-6.18) at `e92c3f1`, Linux 6.18.38.
- Tools: [diamaneos-tools](https://github.com/DiamaneOS/diamaneos-tools) at `7ce3748`, production kernel configuration policy.
- 288 modules (43 left out by policy), 1 device tree, 95 overlays.
- Built 31 October 2026.

## Contents

| Path | What it is |
| --- | --- |
| `Image` | The kernel |
| `dtbs/`, `dtbo.img` | Device tree and overlays |
| `modules/` | Kernel modules, stripped and signed |
| `BoardConfigKernel.mk` | Which modules go to vendor_boot, vendor_dlkm and system_dlkm, and their load order |
| `device-kernel.mk` | Installs the kernel |
| `*-modules.blocklist` | Modules that must not load |

## Module signatures

- The kernel only loads modules signed with its own key.
- Each build makes a new key. The private half stays on the build machine.
- A rebuild from the same sources matches these files except for the module
  signatures.

## Building it yourself

See [FP6-KERNEL.md](https://github.com/DiamaneOS/diamaneos-tools/blob/main/docs/FP6-KERNEL.md)
in the tools repository: `diamaneos kernel prepare` and `diamaneos kernel build`
make this set from the pinned sources.

## Licence

The kernel and its modules are GPL-2.0 (some modules dual-licensed). The
sources are at the revisions above.
