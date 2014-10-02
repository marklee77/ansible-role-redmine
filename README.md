marklee77.redmine
================

The purpose of this role is to install redmine to a web server and enable access
with nginx. This install uses the MySQL backend rather than Postgres. The redmine
server name can be specified by changing the redmine_hostname variable in
vars/main.yml.

This has only been trusted on Ubuntu trusty. It will not work as-is on precise
as redmine requires ruby 1.9 and precise uses ruby 1.8 as the system binary.
Thus, this role is not currently being tested with travis.

Role Dependencies
-----------------

- marklee77.modules-extra

Role Variables
--------------

- redmine_mysql_host: localhost

- redmine_root_mysql_password: root mysql password
- redmine_git_mysql_password: git mysql password, will be set to a random value 
                             by default
- redmine_hostname: hostname that redmine will service, will be set to "localhost" by
                   default


- redmine_checkout_version: 7-1-stable

- redmine_ssh_hostname: "{{ redmine_hostname }}"
- redmine_ssh_port: 22
- redmine_http_port: 80
- redmine_https_port: 443
- redmine_enable_ssl: true
- redmine_require_ssl: true

- redmine_ssl_cert_file: 
- redmine_ssl_key_file: 


- redmine_admin_email: "git@localhost.localdomain"
- redmine_admin_name: Administrator
- redmine_admin_username: root
- redmine_admin_password: password
- redmine_admin_theme_id: "redmine::Theme::MARS"

- redmine_signup_enabled: false

Example Playbook
-------------------------

    - hosts: all
      sudo: True
      roles:
        - marklee77.mariadb
        - marklee77.redmine

Try it Out
---------------------------

Check out the github repository, vagrant up, and load http://localhost:8080 in
your web browser.

License
-------

GPLv2

Author Information
------------------

http://stillwell.me

