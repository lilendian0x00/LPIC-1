**1. On Linux systems, where are the files for the GRUB bootloader stored?**
Under `/boot/grub`

**2. Where should the boot partition end to ensure that a PC will always be able to load the kernel?**

before cylinder 1024 (528MB)

**3. Where is the EFI partition usually mounted?**
under the `/boot/efi`

**4. When manually mounting a filesystem, under which directory should it usually be mounted?**

under the `/mnt`, However, this is not mandatory. You can mount a partition under any directory you want.


**5. What is the smallest unit inside of a Volume Group?**
Volume Groups are subdivided into Logical extents (LE) 


**6. How is the size of a Logical Volume defined?**
The size of a logical volume is defined as the size of physical extents (4MB by default) multiplied by the number of extents on the volume.

**7. On a disk formatted with the MBR partitioning scheme, which is the ID of the EFI System Partition?**

`0xEF`

**8. Besides swap partitions, how can you quickly increase swap space on a Linux system?**
Swap files can be used.
