**1. What is the command to install a package named `package.deb` using dpkg?**
`dpkg -i package.deb`

**2. Using `dpkg-query`, find which package contains a file named 7zr.1.gz.**
`dpkg-query -S 7zr.1.gz`

**3. Can you remove a package called unzip from the system using `dpkg -r unzip` if the package file-roller depends on it? If not, what would be the correct way to do it?**

No, you can't. you must first remove `file-roller` and then `unzip` So:
`dpkg -r unzip file-roller`


**4. Using apt-file, how can you find out which package contains the file `unrar`?**

`apt-file search /usr/bin/unrar`

**5. Using apt-cache, what is the command to show information for the package gimp?**

`apt-cache show gimp`


**6. Consider a repository with Debian source packages for the `xenial` distribution, hosted at http://us.archive.ubuntu.com/ubuntu/ and with packages for the universe component. What would be the corresponding line to be added to `/etc/apt/sources.list`?**

`deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe`

This line could also be added inside a .list file in `/etc/apt/sources.list.d/`. The name is up to you but should be descriptive, something like `xenial_sources.list`.

**7. While compiling a program, you come across an error message complaining that the header file `zzip-io.h` is not present on your system. How can you find out which package provides that file?**

`apt-file search zzip-io.h`

**8. How can you ignore a dependency warning and remove a package using dpkg, even if there are packages that depend on it in the system?**
The parameter `--force` can be used, but this should never be done unless you know exactly what you are doing, since there is a great risk that your system will be left in an inconsistent or “broken” state.

**9. How can you get more information about a package called `midori` using `apt-cache`?**
`apt-cache show midori`

**10. Before installing or updating packages with apt-get, which command should be used to ensure that the package index is up-to-date?**
`apt-get update` This will download the **latest package indexes** from the repositories described in the `/etc/apt/sources.list` file or in the
`/etc/apt/sources.list.d/` directory.



