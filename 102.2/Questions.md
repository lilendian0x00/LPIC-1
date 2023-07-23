**1. What is the default location for the GRUB 2 configuration file?**
`/boot/grub/`

**2. What are the steps needed to change the settings for GRUB 2?**
changing `/etc/default/grub` and then do `update-grub` which is equal to `grub-mkconfig -o /boot/grub/grub.cfg` 

**3. Into which file should custom GRUB 2 menu entries be added?**
For GRUB2 we must edit files inside `/etc/grub.d/` and add our custom menu entries to it like `/etc/grub.d/40_custom.`

**4. Where are the menu entries for GRUB Legacy stored?**
For GRUB Legacy we must edit `/boot/grub/menu.lst` 

**5. From a GRUB 2 or GRUB Legacy menu, how can you enter the GRUB Shell?**
In the menu entry press `c`

**6. Imagine a user configuring GRUB Legacy to boot from the second partition of the first disk. He writes the following custom menu entry:**
```Bash
title My Linux Distro
root (hd0,2)
kernel /vmlinuz root=/dev/hda1
initrd /initrd.img
```
**However, the system will not boot. What is wrong?**

The boot partition is wrong and unlike GRUB2, GRUB Legacy counts the partitions from zero. So, the correct command for the second partition of the first disk should be `root (hd0,1)`.

**7. Imagine you have a disk identified as `/dev/sda` with multiple partitions. Which command can be used to find out which is the boot partition on a system?**

`fdisk -l` The boot partition will be marked with an asterisk (`*`) in the listing.

**8. Which command can be used to find out the UUID of a partition?**
`ls -la /dev/disk/by-uuid/`

**9. Consider the following entry for GRUB 2**

```Bash
menuentry "Default OS" {
    set root=(hd0,1)
    linux /vmlinuz root=/dev/sda1 ro quiet splash
    initrd /initrd.img
}
```
**Change it so the system will boot from a disk with the UUID** `5dda0af3-c995-481a-a6f3-46dcd3b6998d`?

```Bash
menuentry "Default OS" {
    search --set=root --fs-uuid=5dda0af3-c995-481a-a6f3-46dcd3b6998d
    linux /vmlinuz root=/dev/sda1 ro quiet splash
    initrd /initrd.img
}
```

**10. How can you set GRUB 2 to wait for 10 seconds before booting the default menu entry?**
Change the `GRUB_TIMEOUT` parameter in `/etc/default/grub` to `GRUB_TIMEOUT=10` and do `update-grub`

**11. From a GRUB Legacy shell, what are the commands to install GRUB to the first partition of the second disk?**

```Bash
grub> root (hda1, 0)
grub> setup (hda1)
```

