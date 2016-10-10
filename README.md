# Minimalistic rEFInd theme

## Forked for my own use. You can use it too, but at YOUR OWN RISK!


[rEFInd](http://www.rodsbooks.com/refind/) is a simplistic boot manager for UEFI based systems. This is a clean and minimal theme for it.

![rEFInd Minimalistic](http://i.imgur.com/y9dR4Qp.png)
  
---

### Installation

1. Clone this git to a place where you can change the files easily. So, for example, your Documents directory.

2. Find your rEFInd directory. It should be one of these:
 * `/boot/EFI/refind`
 * `/boot/efi/EFI/refind`
 * `/boot/EFI/BOOT`
 * `/boot/efi/EFI/BOOT`
 
 The one used in these files and example is `/boot/EFI/BOOT`, so pay attention in case yours is different.

3. Open your terminal in the directory with `README.md`.

4. Do `sudo blkid` to see the PARTUUID of your root partition and change it in `put.conf`. If you don't have `intel-ucode.img` in your ESP, remove it from the options of each entry too.

5. Make sure everything in the `put.conf` and `theme/theme.conf` files is correct for what you want (The default menu entries are disabled by default, so if you're using them, enable them).

6. **MAKE SURE EVERYTHING IS RIGHT!**

7. Do `su`.

8. Do `cp -r theme /boot/EFI/BOOT`.

9. Do `cat put.conf >> /boot/EFI/BOOT/refind.conf`.

10. Do `exit`. You're done.

---

### Example

Here's the example menuentry configuration that comes in `put.conf` (They're all disabled for safety).

```nginx
menuentry "Arch" {
	icon /EFI/BOOT/theme/icons/os_arch.png
	loader /vmlinuz-linux
	initrd /initramfs-linux.img
	options "root=PARTUUID=41548379-ce00-45b3-b18d-8b5ee699d3c7 rw initrd=/intel-ucode.img"
	disabled
}

menuentry "Arch - CLI" {
	icon /EFI/BOOT/theme/icons/os_arch_cli.png
	loader /vmlinuz-linux
	initrd /initramfs-linux.img
	options "root=PARTUUID=41548379-ce00-45b3-b18d-8b5ee699d3c7 rw initrd=/intel-ucode.img systemd.unit=multi-user.target"
	disabled
}
```

Entries that are autodetected should also show the proper icons.

If you want a terminal icon in some of the entries, you have to add `_cli` just the before the dot on the icon of a menu entry, like so:
 ```nginx
menuentry "Arch - CLI" {
	icon /EFI/BOOT/theme/icons/os_arch_cli.png
```
This doesn't work with the Mac and Windows icons.

---

### TODO
* MOAR ICONS!!!!!

---

### Attribution

The original rEFInd-minimal theme is from [Evan Purkhiser][evan]. Check it out [here][minimal]. 
This README is also based on his'.

[evan]: https://github.com/EvanPurkhiser
[minimal]: https://github.com/EvanPurkhiser/rEFInd-minimal
