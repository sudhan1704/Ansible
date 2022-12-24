# Ansible

  - Configuration management tool - allows you to configure potentially a whole network of computers at once.
  - Ansible tool is wriiten in python.
  - Playbook is wriiten in YAML language as configuration files.
  
## Installing ansible (from epel repository)

    yum install ansible 
    
    
## To check the version of ansible 

    ansible --version

To change certain settings of ansible, go to ansible configuration file in the path /etc/ansible/ansible.cfg

The centralized server (master server) is configured to login to the client servers by adding the ip and the hostname to a inventory file 
in the master server.

    vi /etc/hosts

Add the ip and the hostname of the client servers in the format

192.168.0.113    google.com    google


192.168.0.114    yahoo.com    yahoo


192.168.0.109    bingapp.uk.com    bingapp


The client servers are logged in from the centralized server through ssh. A ssh public and a private key is generated and the public key is given to all the client servers 
while the private key is used by the master server to communicate with the client servers.

  - To generate ssh key command
  
        $ ssh keygen
        
       
To copy the public key generated in the master server to the client servers[hostname of the client servers is used]

    ssh-copy-id [hostname]
    
    
To login into a client server, use the command

    ssh [hostname or ip]
    
    
-------------------------------------------------------------------------------------------------------------------------------

## adhoc commands in ansible

  - Syntax
  
      $ ansible [host_group] -m [module] -a "[arguments]"
     
     Examples
     
      $ ansible multi -m ping -i ansible_hosts – user=vagrant 
      
      $ ansible multi -m command -a uptime 
      
      $ ansible multi -a "free -m" -i ansible_hosts


## Playbooks - (play-file)

using scripts

All commands are written in a single file and executed at once

YAML Syntax

surf ansible yaml syntax documentation

    - Example
    
      -  Install httpd package - yum module

        ---  
        - name: install the latest version of Apache
          yum:
            name: httpd
            state: latest


create a text file to copy and save the playbook

vi play1.yml                ---(save the file as .yml or .yaml - must)

  - To execute the play
  
    $ ansible-playbook play1.yml







    
    
    
    
    
    
    
    
    
    
    
    
    


   

    
   












