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
      
    
    - 2.3 Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123).
      ```
      sudo ufw default deny incoming
      sudo ufw default allow outgoing
      sudo ufw allow 2200/tcp
      sudo ufw allow 80/tcp
      sudo ufw allow 123/udp 
      sudo ufw enable
      ```
      Also add port 123, 80 as Custom in network under Lightsail console.
      




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
