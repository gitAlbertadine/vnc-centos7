=## vnc-centos 7
```
#sudo swapoff -v /swapfile
#remove /swapfile swap swap defaults 0 0 from the /etc/fstab file.
#sudo rm /swapfile

sudo dd if=/dev/zero of=/swapfile bs=32768 count=1048576
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo sh -c 'echo "/swapfile swap swap defaults 0 0" >> /etc/fstab'
sudo vim /etc/sysctl.conf
# add: vm.swappiness=10
----------------
#sudo swapon --show
#sudo free -h
#cat /proc/sys/vm/swappiness
#sudo sysctl vm.swappiness=10

-----------_---=-

sudo useradd -c "User adam Configured for VNC Access" adam
sudo passwd adam
sudo useradd -c "User moha Configured for VNC Access" moha
sudo passwd moha
sudo yum groupinstall -y "GNOME Desktop"
sudo reboot
------_----_---
sudo yum install -y tigervnc-server
#sudo systemctl status vncserver@:.service
#sudo systemctl is-enabled vncserver@.service
#sudo ls -l /lib/systemd/system/vnc*
#sudo ls -l /etc/systemd/system/*.wants/vnc*
#  -doesn't exist
sudo cp /lib/systemd/system/vncserver@.service /etc/systemd/system/vncserver@:4.service

sudo cp /lib/systemd/system/vncserver@.service /etc/systemd/system/vncserver@:5.service

sudo vi /etc/systemd/system/vncserver@:4.service
-_--_-------_----
sudo vi /etc/systemd/system/vncserver@:5.service
sudo systemctl enable vncserver@:4.service
--------_-_--------------

sudo systemctl enable vncserver@:4.service
#sudo firewall-cmd --state
#sudo systemctl start firewalld
sudo firewall-cmd --permanent --zone=public --add-port=5904-5905/tcp
sudo firewall-cmd --reload

#adam: vncserver
-------_--------------------_----
#moha: vncserver
----_-------_---_---------_
sudo systemctl daemon-reload
sudo systemctl restart vncserver@:4.service
sudo systemctl restart vncserver@:5.service
sudo systemctl status vncserver@:4.service
-----------------------_--------
sudo systemctl status vncserver@:5.service
sudo -rm /tmp/.X11-unix/X5 /tmp/.X11-unix/X4
---------------_----------_-
ssh -L 5900:31.187.74.183:5904 adam@31.187.74.183 -N
```
## script
```
#-https://www.golinuxcloud.com/step-by-step-guide-to-configure-tigervnc/

sudo yum groupinstall -y "GNOME Desktop"
sudo dd if=/dev/zero of=/swapfile bs=32768 count=1048576
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo sh -c 'echo "/swapfile swap swap defaults 0 0" >> /etc/fstab'
sudo vim /etc/sysctl.conf
sudo sh -c 'echo "vm.swappiness=10" >> /etc/sysctl.conf'
sudo free -h

sudo yum install -y tigervnc-server
sudo cp /lib/systemd/system/vncserver@.service /etc/systemd/system/vncserver@:1.service
sudo useradd -c "User adam Configured for VNC Access" adam
sudo passwd adam
sudo vim /etc/systemd/system/vncserver@:1.service
#adam

sudo systemctl daemon-reload
su - adam
vncpasswd
exit

sudo systemctl daemon-reload
sudo systemctl enable vncserver@:1.service
sudo systemctl start vncserver@:1.service
sudo firewall-cmd --permanent --zone=public --add-port=5900-5901/tcp
sudo firewall-cmd --reload
sudo -rm /tmp/.X11-unix/X1
sudo firewall-cmd --list-all
#sudo reboot
#cat /proc/sys/vm/swappiness


```





```
