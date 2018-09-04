# Amazon-LighSail-Server
Using a baseline installation of a Linux server and preparing it to host my web application. This includes securing it against a number of attack vectors, installing and configuring a database server and deploying a handmade web application.


## LightSail-Server1
      IP Address: 34.227.56.136
      Port: 2200
      SSH Key: Included the PrivateKey in the "Notes to Reviewer"

## Secure your Server
    Update and Upgrade Packgages:
            $ sudo apt-get update
            $ sudo apt-get udgrade
            
    Change the Default Port (22 to 2200) on SSH connection:
            $ sudo nano /etc/ssh/sshd_config
    
    Configure UFW
        Blocked all incoming and allowed all outgoing:
            $ sudo ufw default deny incoming
            $ sudo ufw allow outgoing
        
        Allow SSH on port 2200, HTTP on port 80, and NTP on port 123:
            $ sudo ufw allow 2200/tcp
            $ sudo ufw allow www
            $ sudo ufw allow ntp
        
        Turn on the firewall:
            $ sudo ufw enable 
            
## Grader user acess
    Create a new user:
        $ sudo adduser grader
    

        
            
    
