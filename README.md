# vnc-centos7
```
-https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-
sudo fallocate -l 32G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo sh -c 'echo "/swapfile none swap sw 0 0" >> /etc/fstab'

remote-access-for-the-gnome-desktop-on-centos-7
sudo useradd -c "User adam Configured for VNC Access" adam
sudo passwd adam
sudo useradd -c "User moha Configured for VNC Access" moha
sudo passwd moha
sudo yum groupinstall -y "GNOME Desktop"
sudo reboot
sudo yum install -y tigervnc-server


```
