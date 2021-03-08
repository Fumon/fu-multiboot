# fu-multiboot
Grub config and setup scripts for making a USB drive which can boot many ISOs and works on ancient BIOS machines.

## Current process

1. Make a drive with a ext2 partition (might work fine with exfat or vfat for convenience) and an MBR partition table. Hybrid might work but would need an EFI partition and a special MBR partition.
2. Mark the partition bootable.
3. Create the filesystem 

```bash
# mkfs.ext2 /dev/sdxx
```

4. Mount the partition
5. Create a folder on the drive for grub and the isos to live

```bash
# mkdir -p <mountpoint>/boot/{grub,isos}
```

6. Install grub to the drive with the support files 

```bash
# grub-install --target=i386-pc --recheck --boot-directory=<mountpoint>/boot/ /dev/sdx
```

7. Copy the grub.cfg from this repo into <mountpoint>/boot/grub
8. Copy over your ISOs
9. Customize grub.cfg
