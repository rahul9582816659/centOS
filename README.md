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


