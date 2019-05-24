# centOS

Run:
---
1. sudo yum check-update
2. sudo yum update
3. restart after this

Sublime:
--------
1. sudo rpm -v --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg
2. sudo yum-config-manager --add-repo https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo
3. sudo yum install sublime-text

NodeJS:
------
1. curl -sL https://rpm.nodesource.com/setup_10.x | sudo bash -
2. sudo yum install nodejs
3. npm install -g @angular/cli

Java:
-----
1. Bydefault installed
2. install java 8 latest from software dir : rpm will be there run that : sudo yum install jdk... 
3. Intellija : /usr/java/1.8... : select this


Maven:
------
1. sudo yum install maven
2. mvn -version
3. The Local Repository : Linux: /home/<User_Name>/.m2 : /home/rahul/.m2

VLC:
----
1. yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
2. yum install https://download1.rpmfusion.org/free/el/rpmfusion-free-release-7.noarch.rpm
3. yum install vlc

Jetbrain Tool:
-------------
1. download tool and run

Docker:
-------
1. sudo yum install -y yum-utils device-mapper-persistent-data lvm2
2. sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
3. sudo yum install docker-ce
4. sudo usermod -aG docker $(whoami)
5. sudo systemctl enable docker.service
6. sudo systemctl start docker.service

7. sudo yum install epel-release
8. sudo yum install -y python-pip
9. sudo pip install docker-compose
10. sudo yum upgrade python*
11. sudo yum remove python-gssapi.x86_64
12. docker-compose version

to run docker using user rahul : 
1. su root
2. usermod -aG docker $(whoami)
3. su rahul


MYSQL:
------
1. download latest version from here 
2. sudo rpm -Uvh mysql80-community-release-el7-3.noarch.rpm : change this to what you download from mysql
3. yum repolist enabled | grep mysql
4. sudo yum install mysql-community-server
5. sudo systemctl start mysqld.service
6. sudo systemctl status mysqld.service
7. sudo grep 'temporary password' /var/log/mysqld.log
8. mysql -uroot -p
9. ALTER USER 'root'@'localhost' IDENTIFIED BY '$Dec2017';


10. sudo yum install mysql-workbench-community
11. sudo yum update mysql-server : if need to upgrade

12. sudo systemctl stop mysqld.service : stop mysql service in case you are not using

13. systemctl is-enabled mysqld
14. systemctl disable mysqld
15. systemctl enable mysqld

Kernel Update:
--------------
https://www.tecmint.com/install-upgrade-kernel-version-in-centos-7/
https://www.howtoforge.com/tutorial/how-to-upgrade-kernel-in-centos-7-server/


uname -sr
rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org
rpm -Uvh http://www.elrepo.org/elrepo-release-7.0-3.el7.elrepo.noarch.rpm
yum --disablerepo="*" --enablerepo="elrepo-kernel" list available
yum --enablerepo=elrepo-kernel install kernel-ml
sudo vi /etc/default/grub
GRUB_DEFAULT=0 : change this
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
sudo grub2-mkconfig -o /boot/grub/grub.cfg
restart os


kubernetes:
-----------
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube
sudo cp minikube /usr/local/bin && rm minikube
rm -rf ~/.minikube


sudo yum install libvirt-daemon-kvm qemu-kvm
sudo systemctl enable libvirtd.service
sudo systemctl start libvirtd.service
sudo systemctl status libvirtd.service
sudo usermod -a -G libvirt $(whoami)
newgrp libvirt
curl -LO https://storage.googleapis.com/minikube/releases/latest/docker-machine-driver-kvm2 && sudo install docker-machine-driver-kvm2 /usr/local/bin/
minikube start --vm-driver kvm2 or minikube config set vm-driver kvm2 & minikube start
minikube status


curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
kubectl version

kubectl cluster-info