# Distro-Logo-Animation-Plymouth
This is a simple Plymouth theme.


# Installation

## Installing plymouth
    # apt-get install plymouth
                or 
    # aptitude install plymouth

## Configuration

    Edit the file /etc/initramfs-tools/modules and add the modesetting for your graphics card:

### For Intel:

    # KMS
    intel_agp
    drm
    i915 modeset=1

### For Nouveau (nVidia):

    # KMS
    drm
    nouveau modeset=1

### For ATI:

    # KMS
    drm
    radeon modeset=1

## Clone this repository.

    # cd /usr/share/plymouth/themes
    # sudo git clone https://github.com/50UM3N/distro-logo-animation-plymouth.git
    
After cloning unzip the frames.zip
    
    # cd distro-logo-animation-plymouth/
    # unzip frames.zip

After installing you can test the theme through (as root, preferably on a tty):

    # plymouthd
    # plymouth --show-splash
    # plymouth --quit


## Set GRUB2/GRUB

Check `/etc/default/grub`. It should include the following:

    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"


Reconfigure GRUB2, if you had to add something:

    # sudo grub2-mkconfig -o /boot/grub2/grub.cfg
                        or 
    # update-grub

## Activate the theme on Kali/Debian

Check that the theme ended up in the right place:

    # sudo plymouth-set-default-theme --list

Set the theme as default:

    # sudo plymouth-set-default-theme -R distro-logo-animation-plymouth

The -R option rebuilds the initrd automatically which is necessary.

## Activate the theme on Ubuntu

Install the theme.

    # sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/distro-logo-animation-plymouth/distro-logo-animation-plymouth.plymouth 100

Select the default theme.

    # sudo update-alternatives --config default.plymouth

Update the initramfs image.

    # sudo update-initramfs -u

Now reboot.

