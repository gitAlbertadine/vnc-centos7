## vnc-centos 7
```
[
sudo swapoff -v /swapfile
-Next, remove the swap file entry /swapfile swap swap defaults 0 0 from the /etc/fstab file.
sudo rm /swapfile

sudo dd if=/dev/zero of=/swapfile bs=32768 count=1048576
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo sh -c 'echo "/swapfile swap swap defaults 0 0" >> /etc/fstab'
sudo swapon --show
sudo free -h
cat /proc/sys/vm/swappiness
sudo sysctl vm.swappiness=10
sudo vim /etc/sysctl.conf
  vm.swappiness=10
]

remote-access-for-the-gnome-desktop-on-centos-7
sudo useradd -c "User adam Configured for VNC Access" adam
sudo passwd adam
sudo useradd -c "User moha Configured for VNC Access" moha
sudo passwd moha
sudo yum groupinstall -y "GNOME Desktop"
sudo reboot
sudo yum install -y tigervnc-server
sudo systemctl status vncserver@:.service
sudo systemctl is-enabled vncserver@.service
sudo ls -l /lib/systemd/system/vnc*
sudo ls -l /etc/systemd/system/*.wants/vnc*
  -doesn't exist
sudo cp /lib/systemd/system/vncserver@.service /etc/systemd/system/vncserver@:4.service

sudo cp /lib/systemd/system/vncserver@.service /etc/systemd/system/vncserver@:5.service

sudo vi /etc/systemd/system/vncserver@:4.service
sudo vi /etc/systemd/system/vncserver@:5.service
sudo systemctl enable vncserver@:4.service
sudo systemctl enable vncserver@:4.service
[
sudo firewall-cmd --state
sudo systemctl start firewalld
sudo firewall-cmd --permanent --zone=public --add-port=5904-5905/tcp
sudo firewall-cmd --reload
]
adam: vncserver
moha: vncserver
sudo systemctl daemon-reload
sudo systemctl restart vncserver@:4.service
sudo systemctl restart vncserver@:5.service
sudo systemctl status vncserver@:4.service
sudo systemctl status vncserver@:5.service
sudo -rm /tmp/.X11-unix/X5 /tmp/.X11-unix/X4





```
