# configuring-linux-server
### Introduction
This is the configuring linux server project for udacity where we configure a aws server instance to serve a web app in my case is item catalog project.
### The IP address: http://3.120.158.240.xip.io/
### SSH port: 2200
### summary of software installed:
- git
- python3
- finger
- apache2
- wsgi_mod
- pip
- pip3
### A summary of configuration/setup changes made:
- PostgreSQL
1- to install it `apt-get install postgresql`
2- then i created the database user `sudo -u postgres createuser catalog`
3- after that i created the database `sudo -u postgres createdb catalog`
4- Giving the user a password
`sudo -u postgres psql`
> psql=# alter user catalog with encrypted password 'udacity';

Granting privileges on database
>psql=# grant all privileges on database catalog to catalog ;
- Apache
to install it write `sudo apt-get install apache2`
- Firewall (UFW)
first before we activate the ufw fairwall
`sudo ufw default deny incoming` then `sudo ufw default allow outgoing` add the firewall rules to only allow the ports 2200 for ssh ,www 80 and ntp 123 change the ssh port by adding a custome port in aws and configure the sshd_config and change the port 22 to 2200 
after all that i did `sudo ufw enable` to activate the firewall.
- mod_wsgi
to install it write `sudo apt-get install libapache2-mod-wsgi`
then i created 2 files code.conf and code.wsgi and i put my coonigurations for virtual host and imports see the resources.

### Resources
- http://flask.pocoo.org/docs/1.0/deploying/mod_wsgi/
- https://serverfault.com/questions/265410/ubuntu-server-message-says-packages-can-be-updated-but-apt-get-does-not-update
- https://stackoverflow.com/questions/14547631/python-locale-error-unsupported-locale-setting
- https://stackoverflow.com/questions/16376035/fatal-could-not-create-work-tree-dir-kivy
- https://medium.com/coding-blocks/creating-user-database-and-adding-access-on-postgresql-8bfcd2f4a91e
- https://www.macworld.com/article/2082021/master-the-command-line-deleting-files-and-folders.html
- http://installion.co.uk/ubuntu/vivid/universe/l/libapache2-mod-wsgi-py3/uninstall/index.html
- https://www.digitalocean.com/community/questions/what-is-the-effect-of-permitrootlogin-no
- https://modwsgi.readthedocs.io/en/develop/user-guides/quick-installation-guide.html
- http://flask.pocoo.org/docs/0.12/installation/
- https://oauth2client.readthedocs.io/en/latest/
- https://stackoverflow.com/questions/34838443/typeerror-sequence-of-byte-string-values-expected-value-of-type-str-found
- https://www.youtube.com/watch?v=Ta7HAvu-GPs

### References:

- UFW docs: https://help.ubuntu.com/community/UFW
- How to setup PostgresQL: https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04
- Flask app - deploy a flask app: https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps
- Apache enable site doc: http://manpages.ubuntu.com/manpages/bionic/man8/a2ensite.8.html
