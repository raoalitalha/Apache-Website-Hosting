# Apache Web Server Setup Project

## Overview
This project demonstrates how to install, configure, and deploy a static website using Apache HTTPD on a Linux machine.

## Steps Included
1. Checking user and system information.
2. Updating the operating system.
3. Installing and configuring Apache HTTPD.
4. Setting up the firewall.
5. Downloading and deploying a sample website.
![image](https://github.com/raoalitalha/demo_server/assets/72371702/ce607998-528f-4ff8-8243-de354f8058f9)

## Commands Used
- `whoami`
- `pwd`
- `hostname`
- `hostnamectl set-hostname`
- `cat /etc/redhat-release`
- `sudo dnf check-update`
- `sudo dnf update -y`
- `rpm -qa | grep httpd`
- `dnf list httpd`
- `dnf install -y httpd*`
- `systemctl status httpd.service`
- `systemctl start httpd.service`
- `systemctl enable httpd.service --now`
- `firewall-cmd --permanent --add-service=http --zone=public`
- `firewall-cmd --reload`
- `wget https://www.free-css.com/assets/files/free-css-templates/download/page290/restoran.zip`
- `cp restoran.zip /var/www/html`
- `unzip restoran.zip`
- `rm -rf restoran.zip`
- `cp -r * ..`
- `rm -rf /bootstrap-restaurant-template/`
- `curl localhost`




## Future Plans
- Deploying two websites on a single machine using Apache.
- Hosting, pushing, and pulling code from Git.

## License
Apache License

