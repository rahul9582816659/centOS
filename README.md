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
3. sudo npm install -g @angular/cli
4. sudo npm install -g npm // to update to latest version 

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

Change the file: /etc/grub2-efi.cfg ( /boot/efi/EFI/centos/grub.cfg) 
Change line "set default=$$$$" to ' set default = "0" ' in the else block. 
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

Openshift:
----------
before this install Docker & Kubernetes

wget https://github.com/openshift/origin/releases/download/v1.5.1/openshift-origin-client-tools-v1.5.1-7b451fc-linux-64bit.tar.gz 
or 
download latest from https://github.com/openshift/origin/releases scroll to end 

install latest one from above
tar –xvf openshift-origin-client-tools-v1.5.1-7b451fc-linux-64bit.tar.gz
mv openshift-origin-client-tools-v1.5.1-7b451fc-linux-64bit oc-tool
mv oc-tool /usr/local/bin
export PATH=/usr/local/bin/oc-tool:$PATH

sudo vi daemon.json : add this { "insecure-registries": ["172.30.0.0/16"] }
sudo systemctl restart docker.service
firewall-cmd --zone=public --add-port=8443/tcp --permanent
firewall-cmd --zone=public --add-port=53/udp --permanent
firewall-cmd --reload

Old Version : ------
oc cluster up —use-existing-config host-data-dir=/usr/data metrics=true image=registry.access.redhat.com/openshift3/ose version=latest
oc cluster down

OpenShift Master:
v1.5.1+7b451fc
Kubernetes Master:
v1.5.2+43a9be4

Use Latest Version: --------
oc cluster up —use-existing-config host-data-dir=/usr/data metrics=true image=d83cea28acf9 version=latest
OpenShift Master:
unknown
Kubernetes Master:
v1.11.0+d4cacc0
OpenShift Web Console:
v3.11.0+ea42280

oc login -u system:admin

oc cluster up
oc cluster down

Torrent:
-------
Download latest epel-release rpm from
http://download-ib01.fedoraproject.org/pub/epel/7/x86_64/ or https://download-ib01.fedoraproject.org/pub/epel/7/x86_64/Packages/q/?C=M;O=A

Install epel-release rpm:
sudo yum install qbittorrent*

Virtual Box:
------------
https://www.itzgeek.com/how-tos/linux/centos-how-tos/install-virtualbox-4-3-on-centos-7-rhel-7.html

1. yum install -y kernel-devel kernel-headers gcc make perl
2. yum -y install wget
3. wget https://www.virtualbox.org/download/oracle_vbox.asc
4. rpm --import oracle_vbox.asc
5. sudo wget http://download.virtualbox.org/virtualbox/rpm/el/virtualbox.repo -O /etc/yum.repos.d/virtualbox.repo
6. sudo yum install -y VirtualBox-6.0
7. systemctl start vboxdrv.service
8. systemctl status vboxdrv.service

Ubuntu :
------
http://ubuntuhandbook.org/index.php/2018/05/replace-left-panel-dock-launcher-ubuntu-18-04/
https://www.youtube.com/watch?v=IEzrs1ZU4R0

Gnome :
------
https://linoxide.com/linux-how-to/install-gnome-shell-extensions-gui-cli/

1. sudo yum install git
2. sudo yum install cmake
3. sudo yum install coreutils
4. sudo yum install jq
5. make dir and clone https://github.com/GNOME/chrome-gnome-shell.git
6. got to that dir : cd chrome-gnome-shell/
7. mkdir build && cd build
8. cmake -DCMAKE_INSTALL_PREFIX=/usr -DBUILD_EXTENSION=OFF ../
9. sudo make install