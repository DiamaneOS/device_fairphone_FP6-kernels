# Fairphone 6 kernel prebuilts

The DiamaneOS kernel, modules and device trees for the Fairphone 6, built from
source with `diamaneos kernel build`. The Android build reads them from
`device/fairphone/FP6-kernel`.

## This build

- Sources: [kernel_qcom-6.1](https://github.com/DiamaneOS/kernel_qcom-6.1) at `38d179d`, Linux 6.1.177.
- Tools: [diamaneos-tools](https://github.com/DiamaneOS/diamaneos-tools) at `cde4077`, production kernel configuration.
- 389 modules (48 left out by policy), 14 device trees, 95 overlays.
- Built 7 October 2026.

## Contents

| Path | What it is |
| --- | --- |
| `Image` | The kernel |
| `dtbs/`, `dtbo.img` | Device trees and overlays |
| `modules/` | Kernel modules, stripped and signed |
| `BoardConfigKernel.mk` | Which modules go to vendor_boot, vendor_dlkm and system_dlkm, and their load order |
| `device-kernel.mk` | Installs the kernel |
| `*-modules.blocklist` | Modules that must not load |

The kernel only loads modules signed with its own key. Each build makes a new
key and keeps the private half on the build machine, so a rebuild from the same
sources matches these files except for the module signatures.

## Building it yourself

See [FP6-KERNEL.md](https://github.com/DiamaneOS/diamaneos-tools/blob/main/docs/FP6-KERNEL.md)
in the tools repository: `diamaneos kernel prepare` and `diamaneos kernel build`
make this set from the pinned sources.

## Licence

The kernel and its modules are GPL-2.0 (some modules dual-licensed); the
sources are at the revisions above.
