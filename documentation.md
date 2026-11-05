# RezzOS Documentation

Welcome to the official documentation for RezzOS. This guide covers installation, building from source, and contribution guidelines.

---

## 1. Installation Guide

*This guide is intended for first-time and non-expert users. The installation of RezzOS is a relatively quick and straightforward process.*

### 1.1 Requirements
Before starting the installation, ensure that your system meets the following requirements:
- A USB flash drive with at least 512 MB of storage capacity.
- A computer equipped with a 64-bit processor.
- At least 1 GB of RAM.
- A working internet connection (if downloading the ISO).

### 1.2 Obtaining the Image
You can obtain the RezzOS installation image in one of two ways:
- Download a prebuilt ISO image from the official [GitHub Releases](https://github.com/Rezzev/RezzOS/releases) page.
- Build the ISO image manually from source by following the instructions in the **Build Guide** below.

### 1.3 Writing to USB
Once the ISO image has been downloaded, write it to a USB flash drive using a suitable tool. Common options include:
- Rufus (Windows)
- Ventoy
- balenaEtcher
- dd (Linux/macOS): `dd if=rezzos.iso of=/dev/sdX bs=4M status=progress`

### 1.4 Booting the System
1. Insert the USB flash drive into the computer.
2. Restart the device and enter the BIOS/UEFI setup or the boot menu.
3. Select the USB drive as the boot device.
4. From the GRUB menu, select the first available option to start the live environment.

### 1.5 Installing to Disk
After the live environment has booted successfully:
1. Right-click on any empty area of the desktop.
2. In the context menu, select **"Install On Disk"**.
3. Follow the on-screen instructions provided by the installer.
4. Carefully select the target disk or partition to avoid data loss.
5. Confirm the installation and wait for the process to complete.
6. Restart the computer and remove the USB drive.

> **Note:** Since the project is still in active development, you may encounter bugs during installation.

---

## 2. Build Guide

Follow this guide to build RezzOS on your PC.

### 2.1 Prerequisites
Clone the repository:
```bash
git clone https://github.com/Rezzev/RezzOS.git
```

Install the required build dependencies (Alpine Linux is strongly recommended):
```bash
apk add build-base flex bison linux-headers elfutils-dev openssl-dev perl bc cpio gzip wget tar grub-bios xorriso qemu-system-x86_64 qemu-img fakeroot gtk+3.0-dev gtksourceview-dev e2fsprogs webkit2gtk-4.1 webkit2gtk-4.1-dev
```

> **Important:** You need Alpine Linux installed either in Docker or directly on your machine. Otherwise, the required tools may not compile correctly under `musl`. You may try building on another musl-based distribution, but Alpine is recommended.

### 2.2 Compilation
Run the build script as root or with sudo/doas:
```bash
sudo ./build.sh
```

The build process will progress through the following stages:
`BusyBox -> Kernel -> Build Programs -> Create rootfs -> Create ISO`

After the build completes successfully, you will have a ready-to-use ISO image.

---

## 3. Post-Installation & Network Configuration

### 3.1 First Boot
After starting RezzOS on real hardware, you may notice that internet access is not available by default. This is expected in the current development stage.

### 3.2 Network Setup
To restore connectivity, configure the network parameters manually through the operating system configuration utility, `rezzconfig`. This process typically takes only a few minutes.

Open the configuration tool and enter the required values according to your network environment. After the parameters are set correctly, the system should be able to access the network normally.

---

## 4. Contributing Guide

Hello! Thank you for deciding to help develop **RezzOS** — a lightweight educational Linux distribution.

### 4.1 Contribution Process
1. **Fork the repository:** Create a fork of the [RezzOS](https://github.com/Rezzev/RezzOS) project in your own account.
2. **Make your changes:** Write documented code. If you modify shell scripts, follow the project’s style and formatting rules.
3. **Commit your changes:** Use clear commit messages in English or Russian. We follow conventional commits (e.g., `feat(pkg): added automatic cache cleanup`).
4. **Submit a Pull Request:** Open a PR describing your changes and wait for review.

---

## 5. Important Notice

RezzOS is currently under active development and is not yet a fully finished product. As such, users should be prepared for possible bugs, instability, or incomplete functionality.

If you encounter any issues, we encourage you to report them via [GitHub Issues](https://github.com/Rezzev/RezzOS/issues) or through the project’s Telegram channel so that they can be reviewed and addressed.

**Recommended User Awareness:**
- Exercise caution when using the system in production or critical workflows.
- Report issues promptly when they are discovered.
- Stay informed about updates and changes in the project documentation.

We appreciate your understanding and support as RezzOS continues to evolve.
