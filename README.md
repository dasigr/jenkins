# Continuous Integration Server
A Continuous Integration and Continuous Delivery Server using Jenkins

## Technology Stack
Ubuntu Server (Xenial64) \
OpenJDK \
Jenkins

## Installation
Follow the commands below for installing Jenkins.

#### Install OpedJDK
```
$ sudo apt-get update
$ sudo apt-get install default-jre
$ java -version
openjdk version "1.8.0_191"
OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.16.04.1-b12)
OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
```

#### Install Jenkins
```
$ wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
$ sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
$ sudo apt-get update
$ sudo apt-get install jenkins
$ /etc/init.d/jenkins status
Correct java version found
● jenkins.service - LSB: Start Jenkins at boot time
   Loaded: loaded (/etc/init.d/jenkins; bad; vendor preset: enabled)
   Active: active (exited) since Wed 2019-04-17 04:35:08 UTC; 38s ago
     Docs: man:systemd-sysv-generator(8)
```

#### Configure Jenkins
Visit http://192.168.66.10:8080 \

Get initial admin password and copy it into the form.
```
$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Install suggested plugins

#### Install PHP
```
$ sudo apt-get install php php-dom php-mbstring php-curl php-mcrypt
$ php --version
PHP 7.0.33-0ubuntu0.16.04.3 (cli) ( NTS )
Copyright (c) 1997-2017 The PHP Group
Zend Engine v3.0.0, Copyright (c) 1998-2017 Zend Technologies
    with Zend OPcache v7.0.33-0ubuntu0.16.04.3, Copyright (c) 1999-2017, by Zend Technologies
```

#### Install Composer
```
$ php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
$ php -r "if (hash_file('sha384', 'composer-setup.php') === '48e3236262b34d30969dca3c37281b3b4bbe3221bda826ac6a9a62d6444cdb0dcd0615698a5cbe587c3f0fe57a54d8f5') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
$ php composer-setup.php
$ php -r "unlink('composer-setup.php');"
$ sudo mv composer.phar /usr/local/bin/composer
$ composer --version
Composer version 1.8.5 2019-04-09 17:46:47
```

#### Enable SFTP on CURL
Add sources (deb-src) in /etc/apt/sources.list .
```
$ vim /etc/apt/sources.list
```

```
$ sudo apt-get install autoconf automake libgnutls-dev libidn11-dev libkrb5-dev libldap2-dev libnss3-dev librtmp-dev libssl-dev libtool python quilt zlib1g-dev
```

Follow some instruction at:
https://askubuntu.com/questions/195545/how-to-enable-sftp-support-in-curl

Check if CURL is enabled with SFTP protocol.
```
$ curl --version
curl 7.47.0 (x86_64-pc-linux-gnu) libcurl/7.47.0 GnuTLS/3.4.10 zlib/1.2.8 libidn/1.32 librtmp/2.3
Protocols: dict file ftp ftps gopher http https imap imaps ldap ldaps pop3 pop3s rtmp rtsp smb smbs smtp smtps telnet tftp
Features: AsynchDNS IDN IPv6 Largefile GSS-API Kerberos SPNEGO NTLM NTLM_WB SSL libz TLS-SRP UnixSockets
```

Check if CURL is enabled with SFTP protocol.
```
$ curl --version
curl 7.47.0 (x86_64-pc-linux-gnu) libcurl/7.47.0 GnuTLS/3.4.10 zlib/1.2.8 libidn/1.32 libssh2/1.5.0 librtmp/2.3
Protocols: dict file ftp ftps gopher http https imap imaps ldap ldaps pop3 pop3s rtmp rtsp scp sftp smb smbs smtp smtps telnet tftp
Features: AsynchDNS IDN IPv6 Largefile GSS-API Kerberos SPNEGO NTLM NTLM_WB SSL libz TLS-SRP UnixSockets
```

#### Generate an SSH key
```
$ vagrant ssh
$ ssh-keygen -t rsa
```

## Reference
Installing Jenkins on Ubuntu (https://jenkins.io/doc/book/installing/#debian-ubuntu) \
Setup Jenkins (https://jenkins.io/doc/book/installing/#setupwizard)

## Sponsors
[A5 Project](https://www.a5project.com) - Web Design and Development

## Maintainers
[Romualdo Dasig](https://github.com/dasigr)

## License
GNU General Public License v3