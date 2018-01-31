# Minimalistic Dark rEFInd Theme

## Forked for my own use. You can use it too, but at YOUR OWN RISK!


[rEFInd](http://www.rodsbooks.com/refind/) is a simplistic boot manager for UEFI based systems. This is a dark, clean, minimal theme for it.

![rEFInd Minimalistic](http://i.imgur.com/IXOzMVM.png)
  
---

### Installation

1. Clone this git to a place where you can change the files easily. So, for example, your Downloads directory.

2. Find your rEFInd directory. It should be one of these:
 * `/boot/EFI/refind`
 * `/boot/efi/EFI/refind`
 * `/boot/EFI/BOOT`
 * `/boot/efi/EFI/BOOT`
 
 If yours is not in this list don't freak out, just pretend it is.
 
 The one used in these files and example is `/boot/EFI/refind`, so pay attention in case yours is different.

3. Open your terminal in the directory with `README.md`.

4. Do `sudo blkid` to see the PARTUUID of your root partition and change it in `put.conf`. If you don't have `intel-ucode.img` in your ESP, remove it from the options of each entry too.

5. Make sure everything in the `put.conf` and `theme/theme.conf` files is correct for what you want (The default menu entries are disabled by default, so if you're using them, enable them).

6. **MAKE SURE EVERYTHING IS RIGHT!**

7. Do `su`.

8. Do `cp -r theme /boot/EFI/refind`.

9. Do `cat put.conf >> /boot/EFI/refind/refind.conf`.

10. Do `exit`. You're done.

---

### Example

Here's the example menu entry configuration that comes in `put.conf` (They're all disabled for safety).

```nginx
menuentry "Arch" {
	icon /EFI/refind/theme/icons/os_arch.png
	loader /vmlinuz-linux
	initrd /initramfs-linux.img
	options "resume=PARTUUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX root=PARTUUID=YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY rw initrd=/intel-ucode.img quiet loglevel=3"
	disabled
}

menuentry "Arch - CLI" {
	icon /EFI/refind/theme/icons/os_arch_cli.png
	loader /vmlinuz-linux
	initrd /initramfs-linux.img
	options "resume=PARTUUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX root=PARTUUID=YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY rw initrd=/intel-ucode.img systemd.unit=multi-user.target"
	disabled
}

menuentry "Windows 10" {
	icon /EFI/refind/theme/icons/os_win.png
	loader /EFI/Microsoft/Boot/bootmgfw.efi
	disabled
}
```

Entries that are autodetected should also show the proper icons.

If you want a terminal icon in some of the entries, you have to add `_cli` just before the dot on the icon of a menu entry, like so:
 ```nginx
menuentry "Arch - CLI" {
	icon /EFI/refind/theme/icons/os_arch_cli.png
```
This doesn't work with the Mac and Windows icons.

---

### Icons

|Antergos|Antergos - CLI|Arch|Arch - CLI|
|:---:|:---:|:---:|:---:|
|![Antergos Logo](http://imgur.com/xurqQVh.png)|![Antergos - CLI Logo](http://imgur.com/1lo1P3A.png)|![Arch Logo](http://imgur.com/ViYuPHe.png)|![Arch - CLI Logo](http://imgur.com/YkoEbrN.png)|

|Debian|Debian - CLI|elementary|elementary - CLI|
|:---:|:---:|:---:|:---:|
|![Debian Logo](http://imgur.com/CESYc0M.png)|![Debian - CLI Logo](http://imgur.com/kyEB7Zj.png)|![elementary Logo](http://imgur.com/zecQ18v.png)|![elementary - CLI Logo](http://imgur.com/78LOw0K.png)|

|Fedora|Fedora - CLI|Kubuntu|Kubuntu - CLI|
|:---:|:---:|:---:|:---:|
|![Fedora Logo](http://imgur.com/yr108gd.png)|![Fedora - CLI Logo](http://imgur.com/O3k9Ar7.png)|![Kubuntu Logo](http://imgur.com/xqw1nem.png)|![Kubuntu - CLI Logo](http://imgur.com/0N93ZzX.png)|

|Linux Mint|Linux Mint - CLI|Lubuntu|Lubuntu - CLI|
|:---:|:---:|:---:|:---:|
|![Linux Mint Logo](http://imgur.com/bLsUq9a.png)|![Linux Mint - CLI Logo](http://imgur.com/CK6bTJb.png)|![Lubuntu Logo](http://imgur.com/SdJOJ46.png)|![Lubuntu - CLI Logo](http://imgur.com/sYAPg5P.png)|

|Manjaro|Manjaro - CLI|openSUSE|openSUSE - CLI|
|:---:|:---:|:---:|:---:|
|![Manjaro Logo](http://imgur.com/POFpb8s.png)|![Manjaro - CLI Logo](http://imgur.com/g5biRjX.png)|![openSUSE Logo](http://imgur.com/p9aVJmK.png)|![openSUSE - CLI Logo](http://imgur.com/jrRrT1n.png)|

|Ubuntu|Ubuntu - CLI|Ubuntu GNOME|Ubuntu GNOME - CLI|
|:---:|:---:|:---:|:---:|
|![Ubuntu Logo](http://imgur.com/M7HoZ33.png)|![Ubuntu - CLI Logo](http://imgur.com/ZFrjPBE.png)|![Ubuntu GNOME Logo](http://imgur.com/TmXBMUv.png)|![Ubuntu GNOME - CLI Logo](http://imgur.com/QqJw57c.png)|

|Ubuntu MATE|Ubuntu MATE - CLI|Xubuntu|Xubuntu - CLI|
|:---:|:---:|:---:|:---:|
|![Ubuntu MATE Logo](http://imgur.com/XXnXdt1.png)|![Ubuntu MATE - CLI Logo](http://imgur.com/JhJ1fiy.png)|![Xubuntu Logo](http://imgur.com/0yDVCIh.png)|![Xubuntu - CLI Logo](http://imgur.com/m8mswX8.png)|

|Windows|Mac|
|:---:|:---:|
|![Windows Logo](http://imgur.com/HXO5KP1.png)|![Mac - CLI Logo](http://imgur.com/FOL5obb.png)|

If you want more icons, feel free to ask for them.

---

### Attribution

The original rEFInd-minimal theme is from [Evan Purkhiser][evan]. Check it out [here][minimal]. 
This README is also based on his'.

[evan]: https://github.com/EvanPurkhiser
[minimal]: https://github.com/EvanPurkhiser/rEFInd-minimal
