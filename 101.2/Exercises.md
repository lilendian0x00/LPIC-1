# Guided Exercises

**1. On a machine equipped with a BIOS firmware, where is the bootstrap binary located?**

In the MBR of the first storage device, as defined in the BIOS configuration utility.
The first 440 bytes?

**2. UEFI firmware supports extended features provided by external programs, called EFI applications. These applications, however, have their own special location. Where on the system would the EFI applications be located?**

On the ESP (EFI System partition) located at any available storage
block with a compatible filesystem (usually a FAT32 filesystem).

**3. Bootloaders allow the passing of custom kernel parameters before loading it. Suppose the system is unable to boot due to a misinformed root filesystem location. How would the correct root filesystem, located at `/dev/sda3`, be given as a parameter to the kernel?**

root=/dev/sda3

**4. The boot process of a Linux machine ends up with the following message:**
`ALERT! /dev/sda3 does not exist. Dropping to a shell!`
**What is the likely cause of this problem?**

The kernel was unable to find the device /dev/sda3, informed as the root filesystem.

# Explorational Exercises

**1. The bootloader will present a list of operating systems to choose from when more than one operating system is installed on the machine. However, a newly installed operating system can overwrite the MBR of the hard disk, erasing the first stage of the bootloader and making the other operating system inaccessible. Why would this not happen on a machine equipped with a UEFI firmware?**

Well, because UEFI firmware doesn't uses the hard disk’s MBR to store the first stage of the bootloader.

**2. What is a common consequence of installing a custom kernel without providing an appropriate `initramfs` image?**

The root filesystem may be inaccessible if its type was compiled as an **external kernel module**.

**3. The initialization log is hundreds of lines long, so the output of dmesg command is often piped to a pager command — like command `less` — to facilitate the reading. What dmesg option will automatically paginate its output, eliminating the need to use a pager command explicitly?**

Commands `dmesg -H` or `dmesg --human` will **enable the pager** by default.

**4. A hard drive containing the entire filesystem of an offline machine was removed and attached to a working machine as a secondary drive. Assuming its mount point is `/mnt/hd`, how would `journalctl` be used to inspect the contents of the journal files located at `/mnt/hd/var/log/journal/`?** 

With commands `journalctl -D /mnt/hd/var/log/journal` or `journalctl --directory=/mnt/hd/var/log/journal`
