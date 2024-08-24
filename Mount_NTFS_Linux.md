### MY way of `mounting` NTFS partions to Linux
---
#### Prerequisties:
- To install ntfs-3g and fuse on `Ubuntu`, `Debian`, and `Linux Mint`:
```
 sudo apt update
 sudo apt install ntfs-3g fuse
```
- To install ntfs-3g and fuse on `CentOS`, `Fedora`, `AlmaLinux`, and `Red Hat`:
```
 sudo dnf install ntfs-3g fuse
```
- To install ntfs-3g and fuse on `Arch Linux` and `Manjaro`:
```
 sudo pacman -S ntfs-3g fuse
```
---
#### Mount NTFS partition on Linux:
- We will use the `parted` command to identify the path through which our NTFS partition is accessed.
```
 sudo parted -l
```
Here my NTFS partitions are `/dev/nvme0n1p3` and `/dev/nvme0n1p4`.

- Then, create the path where you plan to mount the partition, if it hasn’t already been created.
```
 sudo mkdir /mnt/ntfs_partition3
 sudo mkdir /mnt/ntfs_partition4
```
- The most basic mount command would look like this. It should mount your NTFS partition with read and write permissions. This is probably the only command that most users will need.
```
 sudo mount -t ntfs /dev/nvme0n1p3 /mnt/ntfs_partition3
 sudo mount -t ntfs /dev/nvme0n1p4 /mnt/ntfs_partition4
```
- To verify the mount and the permissions that it has, use the mount command.
```
 mount | grep ntfs
```
---
#### Mount NTFS partition automatically
- To make the NTFS partition mount automatically on startup, we’ll need to add a line to the `/etc/fstab` file on our system. Use `nano` or your favorite text editor to open it up under root permissions.
```
 sudo nano /etc/fstab
```
Then, add the following line to the file, while substituting your own device directory and mount path.
```
/dev/nvme0n1p4  /mnt/ntfs_partition4  ntfs3  auto,nosuid,nodev,nofail,x-gvfs-show  0  0
/dev/nvme0n1p3  /mnt/ntfs_partition3  ntfs3  auto,nosuid,nodev,nofail,x-gvfs-show  0  0
```
- Explanation
File System Type (ntfs3): This uses the Paragon ntfs3 driver, which provides better support for NTFS file systems in the Linux kernel.
Mount Options:
- `auto`: Mount automatically at boot.
- `nosuid`: Do not allow set-user-identifier or set-group-identifier bits to take effect.
- `nodev`: Do not interpret character or block special devices on the file system.
- `nofail`: Do not fail the boot process if the file system cannot be mounted.
- `x-gvfs-show`: Make the partition visible in GNOME-based file managers.
---
After updating the `/etc/fstab file`, you can run `sudo mount -a` to mount the partitions according to the updated configuration.
