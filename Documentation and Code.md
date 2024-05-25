# 1. Hosting a website on Apache

- In this project . I will install, configure the `apache web server` .A static website will be hosted on the `apche server` on my machine.

## Step 1:

First of all i would like to check and confirm the user information. The user who logged in in the system. . I will run the command 

```bash
whoami
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled.png)

On this system the current user logged in has a user account with the name `ali`

---

It is a good practice to check the `current working directory` in the start . So run the command 

```bash
pwd
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%201.png)

- The current working directory is `/home/ali`

---

Moving on let me check the `hostname` of the system. The command is :

```bash
hostname
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%202.png)

- My current hostname is `www.talha.com`. I want to change the hostname to `www.myproject.com`. For that i have to run the following command:

```bash
hostnamectl set-hostname www.myproject.com
```

---

- Check the information about your system
    1. Operating System Information
    - To check the `Linux Release version` of the OS and it’s name we run the command
    
    ```bash
    cat /etc/redhat-release
    ```
    
    ![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%203.png)
    
    We are using the OS `Rocky` .
    
    - To check more details about the `OS` and its different `attributes` run the command :
    
    ```bash
    cat /etc/os-relesae
    ```
    
    ![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%204.png)
    
    - Now I would like to check that my operating system is up to date or not. Is there any new updates available for it. To just check the `updates availabe` for the current `OS` run the command. If your user do not have `root` privileges either add the user in `wheel` or use the `sudo` . Sudo stands for `super user do` :
    
    ```bash
    sudo dnf check-update
    ```
    
    ![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%205.png)
    
    ![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%206.png)
    
    - I consider it important for my current project to  `update`  my `machine` before i deploy the `web server` . For that I will run the command
    
    ```bash
    #To cehck the list of all available updates and size of total update.
    sudo dnf update 
    ```
    
    ![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%207.png)
    
    If i press `y` new updates will be installed , which are in a total size of `1.2 G`
    
    - But i wanted to install them directly without prompting me a confirmation question. So, i will use the command
    
    ```bash
    #Running this command will directly install thepackages without promting for yes or no
    sudo dnf update -y 
    ```
    
    ![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%208.png)
    
    - Installation complete
    
    > ***Note:*** It is consider a good practice to take a `snapshot`  of the machine before any update and upgrade. (snapshot means backup)
    > 
    - I will do rest of my work in `mobaXterm` remote client. I have to create a `SSH session` `security shell session` . Secure Shell protocol use the `port 21`
    - To establish a connection i must know the `ip address` of my machine.
    - To check the `ip address` of my machine i can run the following commands :
    
    ```bash
    # ALl of the following commands will work fine
    ifconfig
    
    ip a
    
    ip add
    ```
    
    ![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%209.png)
    
- The `ip address` of my `machine` is `192.168.1.15`. I will login using the `192.168.1.15` in the `mobaXterm`.

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2010.png)

- This time i logged in as a `root user`

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2011.png)

# Installation of Apache server:

- The apache server package in Linux is called `httpd` .
- To utlize the package we have to `install and configure` the `httpd` so we can host our website.
- Before installation we have to check either the `apache` is already installed in our machine or not. We will run the command :

```bash
# Checking any Apache httpd package is installed or not
rpm -qa | grep httpd
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2012.png)

The image shows that there is no `httpd` apache package is installed. 

- We can check the available `httpd` package by running the command:

```bash
# To check the package availability and version number 
dnf list httpd
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2013.png)

- The output shows that there is one package available. But, we have to keep ourself on safe side. Sometimes, a software package has other dependencies without it the main package does not work. We can check the other packages and dependencies by running the command

```bash
dnf list httpd*
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2014.png)

- To install the `apache httpd` and it’s related dependencies we run the command :

```bash
dnf install -y httpd*
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2015.png)

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2016.png)

- After the installation is complete we can run the following command to check wither the package and its dependencies are installed completely:

```bash
rpm -qa | grep httpd*

OR

dnf install httpd*
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2017.png)

- The image shows that the packages are installed on the system.
- Now , we will check the `status` of our `http server` by running the command:

```bash
systemctl status httpd.service
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2018.png)

- To `activate` the `httpd server` we will run the command:

```bash
systemctl start httpd.service
```

- When you will run the `systemctl start httpd.servce` command and it does not show any error message. This shows that the service has started. To check it run the `status` command again:

```bash
systemctl status httpd.service
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2019.png)

- The `httpd service` is up and running. To allow it to start as the system start we use the `enable` command.

```bash
systemctl enable httpd.service --now 
```

- Similarly if we  to `stop, restart, relaod and  disable` a service we can do that using the  following commands:

```bash
#To stop a service
systemctl stop httpd.service

#To restart a service
systemctl restart httpd.service

#To reload a service
systemctl restart httpd.service

#To disbale a service
systemctl diable httpd.service

```

- The website code after the installation of `apache server` will be placed in `cd /var/www/html`

# Setting up firewall in machine and adding HTTP port to firewall:

- The default port for the `http` is `80`. To make it running in our machine we have to add the `port 80` to our firewall.
- In Linux firewall is already installed and enabled. But there is a possibility that it might be turned of some reason. So, it is a good practice to always check the firewall. In Linux pre-installed firewall is called `firewalld`. Although there are some lighter version of firewall `e.g ufw` is available. But it is recommended to use the `firewalld`
- Check the current status of firewall by running the status command :

```bash
#These both comamnds will give same results
systemctl status firewalld

OR

 systemctl status firewalld.service
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2020.png)

- As we have checked that the `firewalld` is up and running. Now we ill add the `http`to our firewall. The command is:

```bash
firewall-cmd --permanet --add-service=http --zone=public
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2021.png)

- After successfully adding the `http` on the firewall. It is necessary to `reload` the firewall.

```bash
firewall-cmd --reload
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2022.png)

- To check the list of all the services added to firewall we run the following command :

```bash
firewall-cmd --list-all

# or to be specific

firewallcmd --list-services
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2023.png)

# Download a Sample Website:

- For our project and practice we will dowload the code of the website from a website. Which we ill deploy on our `apache server.
- Some website offers free code of `websites` we can download the code from those website as per our choice.
- Let’s download a code from the website [`https://www.free-css.com/`](https://www.free-css.com/) . I have decided to download the code of the following website:

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2024.png)

The download `url` is [`https://www.free-css.com/assets/files/free-css-templates/download/page290/restoran.zip`](https://www.free-css.com/assets/files/free-css-templates/download/page290/restoran.zip)

- To download the `template` direct in my `Linux Machine` i will use the `wget` command. I will run the following command to download the `zip` file of the code:

```bash
wget https://www.free-css.com/assets/files/free-css-templates/download/page290/restoran.zip
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2025.png)

- The code of the website is downloaded as file name `restoran.zip`

# Moving to code to the `apache` file systema and unzipping:

- To utilize the code  for the `apache server` and host the website. We have to move the `downloaded file` from our `/root/home` to the directory `var/www/html`. We can use the `mv` to completely move the file. Also, we can use the `cp` copy command to keep the file on the `home directory` as well as in the desired directory. I will go for the `cp` command:

```bash
cp restoran.zip /var/www/html
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2026.png)

- After copying and checking now i will `unzip` the code . First go to the directory `/var/www/html` . Now unzip the code using the command `unzip restoran.zip`

```bash
unzip restoran.zip
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2027.png)

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2028.png)

- We can remove the `zip file` which is named as `restoran.zip` . Run the command :

```bash
rm -rf restoran.zip
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2029.png)

- Now, we have to copy all the files present in the unzipped folder which is `cd /var/www/html/bootstrap-restaurant-template/`.
- When in folder``/var/www/html/bootstrap-restaurant-template/`run the following copy command to copy all the content of the folder to its parent directory. Which in current stage will be `/var/ww/html` . The command is :

```bash
cp -r * ..
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2030.png)

- We can now remove the directory `/bootstrap-restaurant-template/`. Run the command :

```bash
rm -rf /bootstrap-restaurant-template/
```

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2031.png)

> It is a good practice to restart the `http service` after deploying your website. Run the command `systemctl restart httpd.service`
> 
- The `website` is `up and hosted` we can check it on our terminal first using the command

```bash
curl localhost

#OR use your IP address
curl 192.168.1.15
```

- We can open the `web browser` e.g `chrome or firefox` and use our `ip address` which is `192.168.1.15` to check the website is running.

![Untitled](1%20Hosting%20a%20website%20on%20Apache%20588703ed2ada430d9a69f7a1767b8225/Untitled%2032.png)

---
