# Our continuing journey of decentralizing the web and replacing hulking giants with flourishing communities

## Installing arch linux on Raspberry Pi 1 Model B Revision 2

Do exactly as [this website](https://archlinuxarm.org/platforms/armv6/raspberry-pi) says. 

* If your SD card is claiming to be read only, and neither fdisk, nor gparted can write it, Manjaro's GUI filesystem viewer can delete it by clicking on format, then selecting erase disk.

## Making arch linux your home

After initializing pacman, as the root user you can now type `pacman -Syyu` for a system upgrade. 

After this is finished, you can create a user by typing `useradd -m [username]` and `passwd [username]`.

Now you can delete the alarm user by deleting it's row in the `/etc/passwd`.

Install sudo by typing `pacman -Syu sudo`.

Add your user to the sudoers file sudoers by typing `visudo` and add this line below the root: `[username] ALL=(ALL) ALL` then quit by pressing `Shift zz`.

Set your root user password by typing `passwd root`.

You can now log out and ssh back in with your username.

Install the following packgages with `sudo pacman -Syu`:

* zsh
* syncthing
* go-ipfs
* git
* vim
* tree

Install oh-my-zsh `sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

When prompted whether to set zsh as your default shell, select 'yes'.

## Setup your usb storage device

1. Plug in your usb device
1. Find it by typing `sudo fdisk -l`
1. Create a desired mountpoint by `mkdir /mnt/your/mount/point`
1. Edit the file responsible for boot time mounts by typing `sudo vim /etc/fstab`
1. Add a line to the table, where <file system> is your device's name listed by fdisk, <dir> is where you want it to be mounted, <type> is either ext4, vfat, fat32 or ntfs, set <options> to default, <dump> to '0' and <pass> to '2' (separate the entrys with tabs, don't worry about it looking wonky and shifted, it will work fine)

 
