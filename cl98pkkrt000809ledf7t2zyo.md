# 13 Independent Linux Distros That are Built From Scratch

Most of them fall into these three categories: Debian, Red Hat (Fedora) and Arch Linux.

Using a distribution based on Debian/Ubuntu, Red Hat/SUSE or Arch Linux has its advantages. They are popular and hence their package manager offers a huge range of software.

However, some users prefer to use Linux distributions built from scratch and be independent of `DEB/RPM` packaging system.

In this article, we will list some of the best Linux distributions developed independently.

# NixOS
![nixos-2022-2048x1280.webp](https://cdn.hashnode.com/res/hashnode/image/upload/v1665762889479/8bluPe9dx.webp align="left")
nitially released in 2003, Nix OS is built on top of the Nix Package Manager. It provides two releases every year, usually scheduled in May and November.

NixOS may not be a distribution directly geared to new and average users. However, its unique approach to package management attracts various kinds of users.

Additionally, 32-bit support systems are also supported.

Key Features:

* Builds packages isolated
* Reliable upgrade with rollback feature
* Reproducible system configuration.

Website:: [NixOS](https://nixos.org/)

# Gentoo
![gentoo-linux-plasma.webp](https://cdn.hashnode.com/res/hashnode/image/upload/v1665763092216/gdD_IWxAC.webp align="left")
Gentoo Linux is an independently developed distribution aimed mainly at system experts. It is built for users who want the freedom to customize, fine-tune and optimize the operating system to suit their requirements.

Gentoo uses Portage package management that lets you create and install packages, often allowing you to optimize them for your hardware. Chromium OS, the open-source version of Chrome OS, uses Gentoo at its core.

Not to forget, Gentoo is one of those distributions that still support 32-bit architectures.

Key Features:

* Incremental Updates
* Source-based approach to software management
* Concept of overlay repositories like GURU (Gentoo’s user repository), where users can add packages not yet provided by Gentoo

Website:: [Gentoo](https://www.gentoo.org/)

# void Linux
![void-linux.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1665763245700/1-jREOFdE.jpg align="left")
Void Linux is a rolling release distribution with its own X Binary Package System (XBPS) for installing and removing software. It was created by Juan Romero Pardines, a former NetBSD developer.

It avoids systemd and instead uses runit as its init system. Furthermore, it gives you the option to use several desktop environments.

Key Features:

* Minimal system requirements
* Offers an official repository for non-free packages
* Support for Raspberry Pi
* Integration of OpenBSD’s LibreSSL software
* Support for musl C library
* 32-bit support

Website:: [void](https://voidlinux.org/)

# Solus ( formerly EvolveOS )
![solus-budgie-2022.webp](https://cdn.hashnode.com/res/hashnode/image/upload/v1665763447900/Q-aZKJ3NZ.webp align="left")
Solus Linux offers some exciting features while built from scratch. Solus features its own homegrown budgie desktop environment as its flagship version.

Compared to other options, Solus Linux is one of the few independent distributions that new Linux users can use. It manages to be one of the best Linux distributions available.

It uses eopkg package management with a semi-rolling release model. As per the developers, Solus is exclusively developed for personal computing purposes.

Website:: [Solus](https://getsol.us/home/)

# Mageia
![mageia-1.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1665763528073/T6g3OlN-a.jpg align="left")
Mageia started as a fork of Mandriva Linux back in 2010. It aims to be a stable and secure operating system for desktop and server usage.

Mageia is a community-driven project supported by a non-profit organization and elected contributors. You will notice a major release every year.

Key Features

* Supports 32-bit system
* Minimal system requirements

Website:: [Mageia](https://www.mageia.org/en/)

# Clear Linux
![clear-linux-desktop.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665763725456/K6ecWDbn-.png align="left")
Clear Linux is a distribution by Intel, primarily designed with performance and cloud use cases in mind.

One interesting thing about Clear Linux is the operating system upgrades as a whole rather than individual packages ( a'la Windows ). So, *even if you mess up with the system accidentally, it should boot correctly, performing a factory reset to let you set it up again.*

It is not geared toward personal use. But it can be a unique choice to try.

Key Features:

* Highly tuned for Intel platforms
* A strict separation between User and System files
* Constant vulnerability scanning

Website:: [Clear Linux](https://clearlinux.org/)

# PCLinuxOS
![pclinuxos.webp](https://cdn.hashnode.com/res/hashnode/image/upload/v1665764124675/CZbvsv7O9.webp align="left")
PCLinuxOS is an x86_64 Linux distribution that uses APT-RPM packages. You can get KDE Plasma, Mate, and XFCE desktops, while it also offers several community editions featuring more desktops.

Locally installed versions of PCLinuxOS utilize the APT package management system thanks to Synaptic package manager. You can also find rpm packages from its repositories.

Key Features:

* mylivecd script allows the user to take a ‘snapshot’ of their current hard drive installation (all settings, applications, documents, etc.) and compress it into an ISO CD/DVD/USB image.
* Additional support for over 85 languages.

Website:: [PCLinuxOS](https://www.pclinuxos.com/?page_id=2)

# 4MLinux

![4m-linux-2022.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1665764184981/aSPwatrkq.jpg align="left")
4MLinux is a general-purpose Linux distribution with a strong focus on the following four “M”  of computing:

* **M**aintenance (system rescue Live CD)
* **M**ultimedia (full support for a huge number of image, audio and video formats)
* **M**iniserver (DNS, FTP, HTTP, MySQL, NFS, Proxy, SMTP, SSH, and Telnet)
* **M**ystery (meaning a collection of classic Linux games)

Key Features

* Support for large number of image, audio/video formats
* Small and general-purpose Linux distribution

Website:: [4MLinux](http://4mlinux.com/index.php?page=home)

# TinyCore Linux

![tinycore.webp](https://cdn.hashnode.com/res/hashnode/image/upload/v1665764474513/UUeu_mssO.webp align="left")
Tiny Core Linux focuses on providing a base system using BusyBox and FLTK. It is not a complete desktop. So, you do not expect it to run on every system.

It represents only the core needed to boot into a very minimal X desktop, typically with wired internet access.

The user gets great control over everything, but it may not be an easy out-of-the-box experience for new Linux users.

Key Features

* Designed to **run from a RAM** copy created at boot time
* By default, operates like a cloud/internet client
* Users can run `appbrowser` to browse repositories and download applications

Website:: [TinyCore](http://www.tinycorelinux.net/)

# Linux From Scratch ( LFS )

![linux-from-scratch.webp](https://cdn.hashnode.com/res/hashnode/image/upload/v1665764660307/fFGrCCrve.webp align="left")
Linux From Scratch is a way to install a working Linux system by building all its components manually. Once completed, it provides a compact, flexible and secure system and a greater understanding of the internal workings of the Linux-based operating systems.

If you need to dive deep into how a Linux system works and explore its nuts and bolts, Linux From Scratch is the project you need to try.

Key Features

* Customised Linux system, entirely from scratch
* Extremely flexible
* Offers added security because of self compile from source

Website:: [LFS](https://www.linuxfromscratch.org/)

# Slackware

![slackware-2048x1280.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1665764769003/rkVQ2JU8i.jpg align="left")
Slackware is the oldest distribution that is still being maintained. Originally created in 1993, with Softlanding Linux System as base, Slackware later became the base for many Linux distributions.

Slackware aims at producing the most UNIX-like Linux distribution while keeping simplicity and stability.

Key Features

* Available for 32-bit and 64-bit systems
* Extensive online documentation
* Can run on Pentium system to latest machines

Website:: [SlackWare](http://www.slackware.com/)

# Alpine

![alpine-linux-xfce-2022.webp](https://cdn.hashnode.com/res/hashnode/image/upload/v1665764906289/uJyn6fysf.webp align="left")
Alpine Linux is a community-developed operating system designed for routers, firewalls, VPNs, VoIP boxes, and servers. It began as a fork of the LEAF Project.

Alpine Linux uses apk-tools package management, initially written as a shell script and later written in C programming language. This is a minimal Linux distribution, which still supports 32-bit systems and can be installed as a run-from-RAM operating system.

Key Features:

* Provides a minimal container image of just 5 MB in size
* 2-year support for the main repository and support until the next stable release for the community repository
* Made around musl libc and Busybox with resource-efficient containers

Website:: [Alpine](https://www.alpinelinux.org/)

# KaOS

![kaos-desktop.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665765024313/6AyQzE7QA.png align="left")
KaOS is a Linux distribution built from scratch and inspired by Arch Linux. It uses pacman for package management. It is built with the philosophy “One Desktop Environment (KDE Plasma), One Toolkit (Qt), One Architecture (x86_64)“.

It has limited repositories, but still, it offers plenty of tools for a regular user.

Key Features:

* Most up-to-date Plasma desktop
* Tightly integrated rolling and transparent distribution for the modern desktop

Website:: [KaOS](https://kaosx.us/)