Ansible: NGINX - PHP (2-Tier)
=============================

Ansible playbook to provision nginx web servers and php (5/7) application servers.

By default, the playbook provisions a `web` and `app` node in the `webservers` and `appservers` groups, respectively, using the following configurations declared in `group_vars/`:

    # group_vars/webservers.yml
    nginx_user: "nginx"
    nginx_vhosts:
      + listen: "80 default_server"
        server_name: "example.com"
        root: "/srv/app"
        index: "index.html"

    # group_vars/appservers.yml
    php_packages:
      + php70w
      + php70w-cli
      + php70w-common
      + php70w-devel
      + php70w-gd
      + php70w-mbstring
      + php70w-pdo
      + php70w-xml
      + php70w-fpm
    ...

OS:
- RHEL/CentOS 6.x.

Roles
-----

- ca-certificates
- git
- libselinux-python
- nginx
- php
- repo-epel-release
- repo-webtatic
- vim

Usage
-----

Clone repo:
    
    $ git clone <repo> ./ansible

Ansible Galaxy install requirements.

    $ ansible-galaxy install -r requirements.yml -p roles/ --ignore-errors

Vagrant
-------

Vagrant up:

    $ vagrant up
