## My way of updating linux kernel to latest version and setting it to defult.

#### NOTE: If something goes wrong although it shouldn't, Don't blame me for your broken system. Simply what I'm trying to say is " Do it at your own risk". 


1\. Firstly check for update ( In my case I'm using Fedora )
```
sudo dnf update -y
```
2\. Now after updating we check the currently installed kernels,
```
sudo dnf list installed kernel
```
This will show a list of the installed kernels on your system.
3\. Okay so here`s the main process of setting the latest kernel as the default starts,
```
ls /boot
```
4\. Now let's remove the old `initramfs` versions here in my case it's,
```
sudo rm /boot/initramfs-6.9.9-200.fc40.x86_64.img 
```
Do the same for `vmlinuz`
```
sudo rm /boot/vmlinuz-6.9.9-200.fc40.x86_64
```
5\. Let's check the installed kernel list once again,
```
sudo dnf list installed kernel
```
Here froom the list we will remove the old installed kernel just like the same as we did above
```
sudo dnf remove kernel-6.9.9-200.fc40
```
6\. Now we must update the `GRUB` configuration to update the kernel
```
sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
```
7\. Alright so our work of setting the latest kernel as the default is all done so let's,
```
reboot
```
And after the successfull reboot you can ckeck the version on terminal with
```
neofetch
```
