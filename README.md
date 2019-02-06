# RaspberryPiLabVIEW
My projects with LabVIEW on a raspberry pi

I followed the installation instructions from makerhub (https://www.labviewmakerhub.com/) and I'm exploring the LINX package to use LabVIEW (2014) on a Raspberry PI.

I use a Raspberry Pi 3 B.

After installing I had 1 issue with downloading my first test to the Raspberry Pi.
It failed on Local IO.lvlib:Load Device Channels downloading the code.

The fix that I found:
> Drop to a command line on the pi and type in the following commands:

> cd /srv/chroot/labview

> sudo schroot --run-session -c lv

> This will drop you into the chroot environment in which labview runs. 

> cd /usr/lib
> ls liblinx*

> This should show you two files, namely liblinxdevice_rpi2.so and liblinxdevice_bbb.so

> If you have three files here, this fix will not work, and there's something else wrong.

> Ok, now we create a symlink called liblinxdevice.so. This symlink should have been created during installation or when first running the > linx environment, but for some reason, it's not.

> Type in ln -s ./liblinxdevice_rpi2.so ./liblinxdevice.so
