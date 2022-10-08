# assesment-ansible
ansibleplaybook for highly available wordpress site
Ansible role that installs and configures WordPress with Apache2.

Features include:

Installation of any WordPress version to specified directory
Configuration of wp-config.php
Fetch random salts for wp-config.php (https://api.wordpress.org/secret-key/1.1/salt/)
Installation
Using ansible-galaxy:

$ ansible-galaxy install labs.wordpress
Using arm (Ansible Role Manager):

$ arm install labs.wordpress
Using git:

$ git clone https://github.com/MalathiJinadoss/assesment-ansible.git
Requirements & Dependencies
Ansible 1.4 or higher
Curl
Variables
Here is a list of all the default variables for this role, which are also available in defaults/main.yml.

wp_version: 6.0.2
wp_install_dir: '/var/www/html'
wp_db_name: "{{ wp_mysql_db }}"
wp_db_user: "{{ wp_mysql_user }}"
wp_db_password: "{{ wp_mysql_password }}"
wp_db_host: 'localhost'
wp_db_charset: 'utf8'
wp_db_collate: ''
wp_table_prefix: 'wp_'
wp_debug: false
wp_admin_email: 'admin@example.com'
wp_webserver: nginx
site_name: "{{ wp_sitename }}"
wp_mysql_db
wp_mysql_user
wp_mysql_password
wp_sitename
These variables are required!

Example playbook
---
- hosts: all
  vars:
    wp_version: 6.0.2
    wp_mysql_db: 'database_name_here'
    wp_mysql_user: 'username_here'
    wp_mysql_password: 'password_here'
    wp_webserver: apache
    wp_sitename: example.com
    wp_admin_email: 'malathijain97@email.com'
    wp_install_dir: "/var/www/{{ wp_sitename }}"
  roles:
    - lab.wordpress
Testing
$ gh repo clone MalathiJinadoss/assesment-ansible
$ cd ansible-role-wordpress
$ vagrant up