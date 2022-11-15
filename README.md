# rpi-ceph-cluster
A Raspberry Pi based ceph cluster

## Reading S.M.A.R.T. data from Seagate USB3 HDDs

The UAS driver in the Linux kernel has ATA command pass through disabled for all Seagate USB drives due to firmware bugs. This also prevents S.M.A.R.T. data to be read from the hard disks and in turn prevents Ceph from correctly monitoring cluster health. The workaround is to switch to the old BOT driver instead, i.a. disabling UAS altogether for the devices. Make sure to adapt the USB device ID below to your own devices as per lsusb.

I still have to figure out whether this somehow adversely impacts performance or reliability but preliminary tests show no problems.

echo "options usb-storage quirks=0bc2:2344:u" | sudo tee /etc/modprobe.d/disable-uas-seagate.conf
sudo update-initramfs -u