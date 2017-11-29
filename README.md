# Linux Server Configuration

This is Udacity sixth project

## about


## Technologies used in the project

## Steps
1. Start a new Ubuntu Linux server instance on [Amazon Lightsail](https://lightsail.aws.amazon.com/ls/webapp/us-east-2/instances/udacity-project/connect?#). 
2. Secure your server
    - 2.1 Update all currently installed packages.
      ```
      sudo apt-get update
      sudo apt-get upgrade
      ```
     
    - 2.2 Change the SSH port from 22 to 2200. Make sure to configure the Lightsail firewall to allow it.
      ```
      sudo nano /etc/ssh/sshd_config
      ```
      change the port from 22 to 2200. Also add port 2200 as Custom in network under Lightsail console.
      <br />
    - 2.3 Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP            (port 123).
      ```
      sudo ufw default deny incoming
      sudo ufw default allow outgoing
      sudo ufw allow 2200/tcp
      sudo ufw allow 80/tcp
      sudo ufw allow 123/udp 
      sudo ufw enable
      ```
      Also add port 123, 80 as Custom in network under Lightsail console.

3. Give grader access.
    - 3.1 Create a new user account named grader.
        ```
        sudo adduser grader
        ```
    
    - 3.2 Give grader the permission to sudo.
        ```
        sudo visudo
        ```
        search the line like `root    ALL=(ALL:ALL) ALL`, and add `grader ALL=(ALL:ALL) ALL`
        
    - 3.3 Create an SSH key pair for grader using the ssh-keygen tool.
        ```
        ssh-keygen
        ```
        login to grader, do following steps:
        ```
        mkdir .ssh
        touch .ssh/authorized_keys
        nano .ssh/authorized_keys
        chmod 700 .ssh
        chmod 644 .ssh/authorized_keys
        ```
        copy from .pub file into authorized_keys
        <br>
        now can login grader using `ssh grader@<ip address> -p 2200 -i ~/.ssh/linux_project`
    
4. deploy project
    - 4.1  Configure the local timezone to UTC.
        ```
        sudo dpkg-reconfigure tzdata
        ```
        select none of above, then set UTC.
     
    - 4.2  Install and configure Apache to serve a Python mod_wsgi application
        ```
        sudo apt-get install libapache2-mod-wsgi python-dev
        sudo apt-get install apache2
        sudo a2enmod wsgi
        ```
    - 4.3 Install and configure PostgreSQL [helpful link](https://www.digitalocean.com/community/tutorials/how-to-secure-postgresql-on-an-ubuntu-vps):  
        ```
        sudo apt-get install postgresql
        ```        
        - a. Do not allow remote connections<br>
        `sudo nano /etc/postgresql/9.5/main/pg_hba.conf` to disable the remote login
        
        
        - b. Create a new database user named catalog that has limited permissions to your catalog application database.
        
        
        
        
        
  



### tools
- python2
- vagrant
- virtual machine

### setup
- install vagrant and  virtual machine
- clone this repo

### running this task
Start the Vagrant by `vagrant up` and then log into it with `vagrant ssh`

run `python lots_of_students_with_user.py` to generate sample public data

To execute the program run `prthon itemCatalog.py` in your terminal

Open `localhost:8000` in your brower in order to do operations



## improvement
- add facebook login
- improve style and layout
- improve data model
