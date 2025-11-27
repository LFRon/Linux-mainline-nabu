Linux mainline kernel for Qualcomm SM8150
============

### Note: Comparing with https://gitlab.com/sm8150-mainline/linux , this kernel added several features which improves the experience for daily use:

1. Add XFS,F2FS Full support
2. Enable PREEMPT_LAZY default, and enable the PREEMPT_DYNAMIC so you can change the PREEMPT mode while Linux is running.
3. Enable Linux kernel module compression with zstd
4. Compress no-need-external-driver from kernel modules into kernel itself
5. Enable SELinux and AppArmor support

### How to build for SM8150 device:  (This is for x86-64 cross compiling)

1. make kernel config: `make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- defconfig sm8150.config`
2. make Image.gz: `make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- Image.gz dtbs`
3. make kernel modules: `make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- modules`
4. install kernel modules to your prefix dir (like ../install): `make ARCH=arm64 CROSS_COMPILE="aarch64-linux-gnu-" modules_install INSTALL_MOD_PATH=../install`

**After compiling, vmlinux (Image) file is at ./arch/arm64/boot**

**Though which could compiling on GCC, but I preferred compile using Clang and turn on Full-LTO which improves performance**
