# Playbook using array variables

##   To view all the declared array variables

        ---
        - hosts: all
          vars:
            basic_vars:
              - sudhan
              - ranjith
              - gopi
              - amudhan
          tasks:
            - name: display_array_variables
              debug:
                msg: "{{ basic_vars }}"

Output:

![image](https://github.com/sudhan1704/raw_images/blob/main/Ansible1.jpg?raw=true)
                
  - To view a single variable
        
        ---
        - hosts: all
          vars:
            basic_vars:
              - sudhan
              - ranjith
              - gopi
              - amudhan
          tasks:
            - name: display_array_variables
              debug:
                msg: "{{ basic_vars [0] }}"

Output:

![image](https://github.com/sudhan1704/raw_images/blob/main/Ansible2.jpg?raw=true)

The variables are numbered from 0 by default, so to print the second or third variable replace 0 with 1 or 2 respectively.

------------------------------------------------------------------------------------------------------------------

## To execute variables that are declared in a file

  - Declare the variables in a file

![image](https://github.com/sudhan1704/raw_images/blob/main/Ansible3.jpg?raw=true)


  - Playbook 
        
![image](https://github.com/sudhan1704/raw_images/blob/main/Ansible4.jpg?raw=true)
        
  - Command to execute a playbook with variables declared in a seperate file
        
            ansible-playbook -i inv -e "@vars.yml" vars_file.yml
            
Output:

![image](https://github.com/sudhan1704/raw_images/blob/main/Ansible5.jpg?raw=true)

---------------------------------------------------------------------------------------------------------------------------

## Loop variable

  - playbook to install a set of packages in a loop
    
    ![image](https://github.com/sudhan1704/raw_images/blob/main/Ansible6.jpg?raw=true)
    
    Output
    
    ![image](https://github.com/sudhan1704/raw_images/blob/main/Ansible7.jpg?raw=true)
    
---------------------------------------------------------------------------------------------------------------------------

## Roles

Step 1 : Create a role directory in the path /home/root [ Example : repo-epel ]
    
    mkdir roles
    cd roles
    
Step 2: 

    - Search the required role in the ansible galaxy webpage or in github (or)

    - To create a role manually in ansible type the command in the path /home/root
    
        ansible-galaxy role init <rolename>
 

Note: Uncomment the "roles path = /etc/ansible/roles" and change the path adress to "/home/root/role" and save in the ansible.cfg file located in /etc/ansible.
Log out and login as root user.


Step 3: Installing repo-epel from ansible galaxy

    ansible-galaxy install geerlingguy.repo-epel
    
Step 4: create a play to create a role with the name of the installed role

![image](https://github.com/sudhan1704/raw_images/blob/main/Ansible8.jpg?raw=true)


Step 4: Execute the playbook

    ansible-playbook -i inv role_example.yml

  - To remove the installed repo use the command

        ansible-galaxy remove geerlingguy.repo-epel

------------------------------------------------------------------------------------------------------------------------------------------------------    


## Ansible vault

To keep sensitive data such as passwords or keys in encrypted files.

  - To create a vault(encripted) file

        ansible-vault create <filename>.yml
        
    Note: When creating a vault file, by default ansible asks to set up a password for the file which is used to view, edit or delete the file.

  - When the vault file is viewed using the command "cat <filename>.yml", only the encripted data is viewed.
  
  - To view the encripted vault file use the following and give the password of the file when prompted.
  
        ansible-vault view <filename>.yml
  
  - To edit the encripted vault file use the following and give the password of the file when prompted.

        ansible-vault edit <filename>.yml

  - To encript an existing YAML file(playbook) use the following command and set up a password

        ansible-vault encript <filename>.yml

  - To encript an existing YAML encripted file(playbook) use the following command and give the password when prompted

        ansible-vault decrypt <filename>.yml
  
  -------------------------------------------------------------------------------------------------------------------------------------------------------









            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            












        


