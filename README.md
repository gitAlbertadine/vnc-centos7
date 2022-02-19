# vnc-centos7
```
-https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-
sudo fallocate -l 32G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo sh -c 'echo "/swapfile none swap sw 0 0" >> /etc/fstab'
[
sudo swapoff -v /swapfile
-Next, remove the swap file entry /swapfile swap swap defaults 0 0 from the /etc/fstab file.
sudo rm /swapfile
sudo dd if=/dev/zero of=/swapfile bs=16384 count=1048576
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo sh -c 'echo "/swapfile swap swap defaults 0 0" >> /etc/fstab'
sudo swapon --show
sudo free -h
]

remote-access-for-the-gnome-desktop-on-centos-7
sudo useradd -c "User adam Configured for VNC Access" adam
sudo passwd adam
sudo useradd -c "User moha Configured for VNC Access" moha
sudo passwd moha
sudo yum groupinstall -y "GNOME Desktop"
sudo reboot
sudo yum install -y tigervnc-server


```
