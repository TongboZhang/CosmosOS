# Notes

## How to add grub menu entry **CORRECTLY**
- Modify ```/etc/grub.d/40_custom``` to add menu entry
    ```sh
    #!/bin/sh
    exec tail -n +3 $0
    # This file provides an easy way to add custom menu entries.  Simply type the
    # menu entries you want to add after this comment.  Be careful not to change
    # the 'exec tail' line above.
    menuentry 'HelloOS' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        multiboot2 /boot/HelloOS.bin
        boot
    }
    ```
- Modify ```/etc/default/grub```to show the grub menu when boot
    ```ini
    GRUB_TIMEOUT_STYLE=menu # not 'hidden'
    GRUB_TIMEOUT=5 # not '0'
    ```
- Run ```sudo update-grub``` to update grub.cfg
- Check whether ```/boot/grub/grub.cfg``` is correctly updated
