# LAMP_Ansible

Ansible playbook including the installation of the LAMP stack (Apache, MySQL, PHP) as well as preparing the system to install Wordpress.

Playbook includes:
--------------
* Installation of additional programs and modules needed to install and run the lamp: ufw, python3, python3-pip, pymysql, unzip
* Installing and configuring Apache web server
* Installing and configuring MariaDB, removing anonymous users, creating a database and user
* PHP installation
* Downloading and unpacking the archive with Wordpress and adding a configuration file

Preparing to launch playbook:
--------------
* it is necessary to have a user with sudo rights on the target computer
* add the ssh public key of the host computer to the file authorized_keys on the target computer
* install MySQL collection for Ansible to work with MariaDB
* edit your inventory file by changing the ansible_host and ansible_user parameters
* edit /etc/sudoers file on the target computer as root with the line %sudo ALL=(ALL:ALL) NOPASSWD:ALL (this item is optional and necessary to run playbook without entering sudo password)

Customizing
--------------
Edit the variables in the file vars/main.yml that correspond to the roles in order to change the settings

For Apche:

* http_host: your domain name.
* http_conf: the name of the configuration file that will be created within Apache.
* http_port: HTTP port, default is 80.

For MariaDB:

* mysql_root_password: user root password
* mysql_db: The name of the database to create
* mysql_user: The name of the created user
* mysql_password: password of the user

For Wodpress:

* wp_link: link to download the wordpress archive

Playbook launch
--------------
In order to start it, you should enter the command ansible-playbook playbook.yml in the terminal (adding -bK and entering the sudo password, if you have not edited /etc/sudoers file)

+++
