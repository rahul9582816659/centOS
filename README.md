# centOS

Run:
---
sudo yum check-update
sudo yum update
restart after this

Sublime:
--------
sudo rpm -v --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg
sudo yum-config-manager --add-repo https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo
sudo yum install sublime-text

NodeJS:
------
curl -sL https://rpm.nodesource.com/setup_10.x | sudo bash -
sudo yum install nodejs
npm install -g @angular/cli

Java:
-----
Bydefault installed

VLC:
----
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
yum install https://download1.rpmfusion.org/free/el/rpmfusion-free-release-7.noarch.rpm
yum install vlc

Jetbrain Tool:
-------------
download tool and run

Docker:
-------
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce
sudo usermod -aG docker $(whoami)
sudo systemctl enable docker.service
sudo systemctl start docker.service

sudo yum install epel-release
sudo yum install -y python-pip
sudo pip install docker-compose
sudo yum upgrade python*
sudo yum remove python-gssapi.x86_64
docker-compose version

to run docker using user rahul : 
su root
usermod -aG docker $(whoami)
su rahul


MYSQL:
------
download latest version from here 
sudo rpm -Uvh mysql80-community-release-el7-3.noarch.rpm : change this to what you download from mysql
yum repolist enabled | grep mysql
sudo yum install mysql-community-server
sudo systemctl start mysqld.service
sudo systemctl status mysqld.service
sudo grep 'temporary password' /var/log/mysqld.log
mysql -uroot -p
ALTER USER 'root'@'localhost' IDENTIFIED BY '$Dec2017';


sudo yum install mysql-workbench-community
sudo yum update mysql-server : if need to upgrade


