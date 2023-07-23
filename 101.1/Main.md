**Bios:** Del, F2, F12

# Commands for Inspection
**lspci:** Show all devices currently connected to the pci bus

Can be disk controller to the motherboard

Can be external graphic card

**lsusb:** Lists USB devices currently connected

input devices, keyboards, pointing devices, removable storage media

**Kernel module:** a software component to control the corresponding device. (Every hardware part requires it)

Drivers: Linux modules related to the hardware devices

**lspci:**
-s: a specific device
-v: verbose
-k: show the used kernel driver

**lsusb:**
-d: a specific device id
-t: show the mapping

**kmod package:**
a large set of tools to handle common tasks with Linux kernel modules -> insert, remove, list, check

**lsmod:** shows all currently loaded modules

3 columns: module, size, used by (depending modules)

**modprobe:** used to load and unload modules
-r: to unload a module (it must not be used by any process)

**modinfo:** shows a description, the file, author, licensee, identification, dependencies, parameters for the given module.
p: shows all parameters and ignores other info Zzz

Customized parameters can be persistent by including them in /etc/modprobe.conf OR in an individual file in:
`/etc/modprobe.d/****.conf`

like:
`/etc/modprobe.d/nouveau.conf`

To block a module from auto loading include it in:

`/etc/modprobe.d/blacklist.conf`

example:
blacklist nouveau


However it's better to create a separate configuration file that will contain settings specific only to the given kernel module.


# Information Files and Device Files

Commands like lsusb, lspci,  lscpu,... act as front-ends to read hardware info stored by OS.

**/proc & /sys** 
these dirs are mount points to filesystems not present in a device partition but in RAM space used by kernel to store runtime configuration and information on running processes.

`/proc/cpuinfo:` detailed info about CPU[s] found by operating system.

`/proc/interrupts:` A list of numbers of the interrupts per IO device for each CPU

`/proc/ioports:` List currently registered I/O port region in use.

`/proc/dma:` Lists the registered DMA (direct memory access) channels in use.


`/sys:` Has the specific purpose of storing device info and kernel data structures, including running processes and configurations.

Files inside the `/sys` dir has the similar roles to those in /proc

`/dev:` Every file in it is associated with a system device, particularly storage devices


**IDE channel:** Used to connect IDE devices such as *hard disk drives* and *CD/DVD drives* to the computer. First one represented by `/dev/hda` partitions identified by `/dev/hda1,2,3,...` 

**Removable devices are handled by the `udev` subsystem**

kernel captures the hardware detection event and passes it to the udev.


**udev:** a device manager program that dynamically creates and manages device nodes in the /dev directory. responsible for the **identification** and **configuration** of the devices already present during machine power-up (coldplug) and while the system is running (hotplug). **relies on SysFS**.

the pseudo filesystem for **hardware related info** mounted in **/sys**.

 
As new devices are detected, udev searches for a **matching rule** in the pre-defined rules stored in the directory `/etc/udev/rules.d/`.



# Storage Devices

**block devices:** storage devices
why? data is read in blocks with different sizes and positions.

Every block device is identified by a file in `/dev` dir.

(`/dev/hda` and `/dev/hdb` are reserved for the **master** and **slave** devices on the first IDE channel)

**second IDE channel:** Starts from `/dev/hdc`

**Old floppy drive:** `/dev/fd0`

**IDE**, **SSD** and **USB** block devices will be prefixed by **sd**.
**e.g.:**  `/dev/sda1`, `/dev/sda2` (in the first IDE channel, master will be `sda` and slave will be `sdb`)


**SD cards:** 
partitions of `/dev/mmcblk0` are `/dev/mmcblk0p1` and `/dev/mmcblk0p2`.

**NVMe devices:** Partitions of `/dev/nvme0n1` are `/dev/nvme0n1p1` and `/dev/nvme0n1p2`.

