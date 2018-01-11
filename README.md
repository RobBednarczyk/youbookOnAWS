# Youbook 1.1 on AWS
**Create your bookshelves and show it to the world!**

# Parameters
- IP: 54.76.129.180
- Complete URL: http://ec2-54-76-129-180.eu-west-1.compute.amazonaws.com

# Used software/libraries
- Apache2 server
```sh
$ sudo apt-get install apache2
```
- Application handler: mod-wsgi
```sh
$ sudo apt-get install libapache2-mod-wsgi
```
- Postgresql database
```sh
$ sudo apt-get update
$ sudo apt-get install postgresql postgresql-contrib
```
- Git
```sh
$ sudo apt-get install git-all
```
- psycopg2
```sh
$ sudo apt-get install python-psycopg2
```
- pip
```sh
$ sudo apt-get install python-pip
```
- Flask
```sh
$ sudo pip install Flask
```
- sqlalchemy
```sh
$ sudo pip install SQLAlchemy
```
- flask_httpauth
```sh
$ sudo pip install flask-httpauth
```
- requests
```sh
$ sudo pip install requests
```
- oauth2client
```sh
$ sudo pip install --upgrade oauth2client
```
- passlib and itsdangerous
```sh
$ sudo pip install passlib
$ sudo pip install itsdangerous
```

# Configuration changes

- ufw firewall setup
```sh
$ sudo ufw default deny incoming
$ sudo ufw default allow outgoing
$ sudo ufw allow ssh
$ sudo ufw allow 2200/tcp
$ sudo ufw allow www
$ sudo ufw allow ntp
$ sudo ufw enable
```

- changed ssh port (/etc/ssh/sshd_config)
```sh
$ sudo vim /etc/ssh/sshd_config
```
(Port 2200) - *added line*
PermitRootLogin no
Passwordauthentication no

- sudo permissions to user 'grader'
```sh
$ sudo nano /etc/sudoers.d/grader
```
grader ALL=(ALL) NOPASSWD:ALL - *added line*

- local timezone to UTC
```sh
$ sudo timedatectl set-timezone UTC
```

- Postgresql database

Added database user: **grader** with permissions to do do CRUD operations on the
database *bookshelves*

- Apache server

*DocumentRoot* and *WSGIScriptAlias* parameters changed

2 files modified: */etc/apache2/sites-available/000-default.conf*
... and */etc/apache2/apache2.conf*
