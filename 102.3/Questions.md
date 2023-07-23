
**2. You have developed a piece of software and want to add a new shared library directory to your system (`/opt/lib/mylib`). You write its absolute path in a file called `mylib.conf.`**

In what directory should you put this file?
`/etc/ld.so/conf/d`

What command should you run to make the changes fully effective?
`ldconfig`

**3. What command would you use to list the shared libraries required by kill?**

`ldd /bin/kill`

**4. `objdump` is a command line utility that displays information from object files. Check if it is installed in your system with which `objdump`. If it is not, please, install it.**

Use `objdump` with the `-p` (or `--private-headers`) option and grep to print the dependencies of glibc:

`objdump -p /lib/x86_64-linux-gnu/libc.so.6 | grep NEEDED`

Use `objdump` with the `-`p (or `--private-headers)` option and `grep` to print the soname of glibc:

`objdump -p /lib/x86_64-linux-gnu/libc.so.6 | grep SONAME`

Use `objdump` with the `-p` (or `--private-headers`) option and `grep` to print the dependencies of Bash:

`objdump -p /bin/bash | grep NEEDED`

