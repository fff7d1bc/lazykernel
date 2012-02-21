lazykernel
==========

Configuration
-------------

Create /etc/lazykernel.conf with ``menu_entry_name``, ``initramfs`` (optional) and ``kernel_params`` (optional). You can use as example ``lazykernel.conf.sample`` or examples below:

Basic::

        menu_entry_name="Gentoo Linux"
        kernel_params='root=/dev/sda2'

Initramfs and rootfs over encrypted lvm::

        menu_entry_name="Gentoo Linux"
        initramfs='initramfs.cpio.gz'
        kernel_params="rootfstype=ext4 luks enc_root=/dev/sda2 lvm root=/dev/mapper/vg-rootfs uswsusp resume=/dev/mapper/vg-swap"

Switches
--------
- list - list all kernel images under /boot
- deploy - copy bzImage to /boot/bzImage-<version> and run ``make modules_install``
- clean - check if there is more than 3 kernels, if so, remove oldest kernels leaving only three newest.
- remove_kernel <version> - remove specified version, like ``lazykernel remove_kernel 3.2.6``
- gen-extlinuxconf - generate new /boot/extlinux/extlinux.conf with all the images from /boot/bzImages-* and if /boot/extlinux/memdisk is present, add entries for all the iso and img files (useful for bios updates via freedos floppy images).
- auto - aka ultra-lazyness-mode, run deploy, clean and gen-extlinuxconf.

Limitations
-----------
lazykernel is a simple bash script, with a lot of limitations, it does presume that your kernel images are under ``/boot/bzImage-*`` mask, it does support extlinux only and propably does not handle most of the possible issues at all. If you found it useful and in any ways lacking something, file a issue and I will poke around to fix this shit.

License
-------
Copyright (c) 2012 Piotr Karbowski <piotr.karbowski@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


