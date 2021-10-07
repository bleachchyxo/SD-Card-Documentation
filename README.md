# SD-Card-Documentation
Just a reminder about how to work woth sd cards

## Locate SD Card

    $ ls /dev/sd*

Output:

    /dev/sda /dev/sda2 /dev/sda4 /dev/sda6 /dev/sda1 /dev/sda3 /dev/sda5 /dev/sda7

Insert the SD Card and type again the same command:

    $ ls /dev/sd*

Output:

    /dev/sda /dev/sda2 /dev/sda4 /dev/sda6 /dev/sdb /dev/sda1 /dev/sda3 /dev/sda5 /dev/sda7

The `/dev/sdb` was added to the output. Meaning thats our SD Card.

## SD Card Formating
To format an SD Card using the terminal you must run the next command:

    $ lsblk

Output:
    
    sda      8:0    0 931.5G  0 disk 
    ├─sda1   8:1    0   512M  0 part /boot/efi
    ├─sda2   8:2    0     1K  0 part 
    └─sda5   8:5    0   931G  0 part /
    sdb      8:16   1  29.8G  0 disk 
    ├─sdb1   8:17   1   256M  0 part /media/user/boot
    └─sdb2   8:18   1  29.6G  0 part /media/user/rootfs
    sr0     11:0    1  1024M  0 rom 
    
Now that we alrady identified the SD Card partition we can proceed to wipe off the info with the following command:

    $ sudo dd if=/dev/zero of=/dev/sdb bs=4096 status=progress

Output:
   
## Bruning an image into a SD Card
Once you have the image you want to burn into the SD Card you type the command:

    $ sudo dd if=FreeBSD-13.0-RELEASE-arm64-aarch64-RPI.img-1 of=/dev/sdb bs=1 status=progress

Output:
    
