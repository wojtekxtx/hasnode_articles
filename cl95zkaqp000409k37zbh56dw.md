# Linux Kernel 6.0 Released

Linux 6.0 kickstarts the 6.x series in fine form, bringing an assortment of performance improvements, new hardware support, security fixes, and the usual grab-bag of file-system tweaks to the fore.

Announcing the release over on the Linux Kernel Mailing List, Linus Torvalds said: “As is hopefully clear to everybody, the major version number change is more about me running out of fingers and toes than it is about any big fundamental changes.”

“But of course there’s a lot of various changes in 6.0 – we’ve got over 15k non-merge commits in there in total, after all, and as such 6.0 is one of the bigger releases at least in numbers of commits in a while.

Interested? Read on :)

# Linux Kernel 6.0 Features
Benchmarking done by Phoronix reveals appreciable performance improvements across Intel Xeon ‘Ice Lake’, AMD Ryzen ‘Threadripper’, and AMD EPYC processors thanks to scheduler changes and other kernel energy tweaks. Seeing Linux squeeze more power while using less power is always a welcome one.

Linux 6.0 also does some mandatory future-proofing by laying groundwork for swathes of upcoming hardware. This include support for Intel’s fourth generation Xeon server chips “Sapphire Rapids”, and their 13th generation “Raptor Lake” core chips.

AMD provides a kernel graphics driver for their RDNA 3 GPU, land a new audio driver for AMD ‘Raphael’ platforms and improve the audio support for AMD ‘Jadeite’ systems. Those noticing keyboard issues on Ryzen 6000 series laptop should, if using Linux 6.0, find things once-again function as expected.

Both the OpenRISC and LoongArch architectures gain support for PCI buses, while RISC-V buffs up its cache block management capabilities using a number of new extensions, including the “Zicbom” extension. RISC-V also ships with a new default configuration capable of running Docker from the get-go.

The (expensive) Lenovo ThinkPad X13s laptop, which runs on the Qualcomm Snapdragon 8cx Gen3, starts to pick up support. The ThinkPad X13s is pre-loaded with Windows 11 for ARM but, with Linux support now in the formative stages, this could be a great reference device for Linux ARM enthusiasts.

Talking of laptops Linux enthusiasts use, some TUXEDO Computers and Clevo laptops had issues with touchpads and keyboard when resuming from suspend in earlier kernel versions. Those are now fixed in Linux 6.0.

New hardware supported includes XP-PEN Deco L drawing tablet, a swathe of sensors on AMD motherboards, including Sensor Fusion Hub support on newer Ryzen laptops, and functional Thunderbolt on Intel Raptor Lake.

Ubuntu’s default file system remains `ext4`, so I wanted to mention that Linux 6.0 enables two new `ioctl()` operations: `EXT4_IOC_GETFSUUID` and `EXT4_IC_SETFSUUID`. These make it possible to get or set the UUID stored in a filesystem superblock.

Other assorted changes in Linux 6.0 include:

* Kernel support for NVMe in-band authentication
* Runtime verification subsystem
* Raspberry Pi 4 V3D kernel driver
* `IO_uring` user-space block driver 
* Buffered writes on XFS file systems
* Send Protocol V2 support for Btrfs
* H.265/HEVC API promoted to stable

Plus a whole lot more.

# Get Linux 6.0
As always, latest kernel is available via [this direct link](https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.0.1.tar.xz)