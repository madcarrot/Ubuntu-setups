# Ubuntu-setups (Dual with Windows on 2 SSDs)

1. Install Ubuntu on one SSD by UEFI on flash drive
2. Install Windows 10 on the other SSD (with DVD or another flash drive)

## Windows will break the GRUB menu from Ubuntu
3. Use the ubuntu bootable flash drive, boot into "Try ubuntu", open terminal and use the following commands: ([Source](https://help.ubuntu.com/community/Boot-Repair))
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```
4. then select "Recommand repair"
5. after fix is done, reboot

## Then install NVIDIA driver
6. press "e" when the GRUB menu appears, and add `nouveau.modeset=0` to the end of the linux line ([Source](http://askubuntu.com/questions/742483/can-not-login-after-nvidia-driver-installation)
7. then go to terminal and execute
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-361
sudo reboot
```
