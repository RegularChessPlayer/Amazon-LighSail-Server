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
            
## Grader User Acess
    Create a new user:
        $ sudo adduser grader
    generate the  keys localy:
        ssh-keygen to generate graderKey.pub and graderKey
    So switched into the grader user-- $ sudo su - grader --and created a subdirectory called '.ssh' and set the owner to the grader user and set the permission to read write and execute only to the grader user:
        $ mkdir .ssh
        $ chown grader:grader /home/grader/.ssh
        $ chmod 700 /home/grader/.ssh
     Finaly I disable root login and force authentication using the key pair, so in the file '/etc/ssh/sshd_config':
        $ sudo service ssh restart
    
## Deploy the Project
        The instance timezone was already set to UTC
        
        Install Apache and the libapache2-mod-wsgi, and the python set up tools packages and then restarted the Apache service:
            $ sudo apt-get install apache2
            $ sudo apt-get install libapache2-mod-wsgi
            $ sudo apt-get install python-setuptools
            $ sudo service apache2 restart        
            
        Install PostgreSQL and then opened the file '/etc/postgresql/9.5/main/pg_hba.conf' to ensure that remote connections weren't allowed.
            $ sudo apt-get install postgresql
            $ sudo nano /etc/postgresql/9.5/main/pg_hba.conf
        
        created a new database and user both named catalog and set the password to catalog. I then gave the catalog user permission to use the catalog database:
            $ sudo su - postgres
            postgres $ psql
            postgres=# CREATE DATABASE catalog;
            # CREATE USER catalog;
            # ALTER ROLE catalog WITH PASSWORD 'catalog'
            # GRANT ALL PRIVILEGES ON DATABASE catalog TO catalog;


## List of any third-party resources you made use of to complete this project 

    https://lightsail.aws.amazon.com/ls/docs/en/articles/getting-started-with-amazon-lightsail
    https://support.rackspace.com/how-to/logging-in-with-an-ssh-private-key-on-linuxmac/
    https://www.digitalocean.com/community/tutorials/how-to-create-a-sudo-user-on-ubuntu-quickstart
    
    

##Install git, clone and setup your Catalog App project and Configure and Enable a New Virtual Host finaly  Create the .wsgi File.





        
        
        


        

        
        
            
    
