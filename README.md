# SpearPhisher
A Web Application to Send and Track Spear Phishing Campaigns

SpearPhisher is made up of 3 components. 
* Django Web Application for Creation and Management
* SMTP Server for sending Emails
* Bottle Web Application for Tracking Responses

For best performance the Web server should **NOT** be run on the default single threaded SQlite DB and web server. In this installation we will use Apache with MOD WSGI and MySQL.  

# Installation

This installation has been tested with a clean install of Ubuntu Server 14.04 using Python 2.7
During installation the following optional elements were selected for installation 

* OpenSSH server
* LAMP Server
* Mail server - Postfix Internet Site

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install python-dev python-pip git libmysqlclient-dev
```

## Prerequisites

###### Mandatory

* Django - 1.8.2
* Python MySQl - 1.2.5
* Bottle - 0.12.8

These can all be installed via pip:

```sudo pip install --upgrade bottle django mysql-python```

###### Optional

The following additions are optional but can be used to enhance the functionality or asthetics of the application

* Admin Bootstrap - sudo pip install admin-bootstraped
* SSLServer - sudo pip install django-sslserver
* Fake Factory - sudo pip install 
* 


## Configuration

###### File Paths

```
cd path/to/spearphisher
git clone https://github.com/kevthehermit/SpearPhisher
cd SpearPhisher
sudo cp var/www/html/* /var/www/html/
sudo cp vhost/panel.conf /etc/apache2/sites-availiable/
```

###### MySql

It is advised to secure your new MySQL install with

```sudo mysql_secure_installation```

Create a user and a database

```
$ mysql -u root -p 
enter password: <The one you set at install>
mysql> create database spearphsiher;
mysql> create user 'spearphisher'@'localhost' identified by 'spearphisher';
mysql> grant all on spearphisher.* to 'spearphisher'@'localhost';
mysql> FLUSH PRIVILEGES;
mysql> quit
```

Edit spearphisher/settings.py

- Modify SECRET_KEY to a random string of 32 characters
- Set the DATABASES Settings to match your setup
- Set Your TIME_ZONE

python manage.py makemigrations
python manage.py migrate

###### Super User

```python manage.py createsuperuser```

Follow the on screen instructions. The username must be in the form of an email address.

## First Run

With all the steps in place you should be able to run the Django web server and access the control panel. 

python manage.py runserver 0.0.0.0:8080

then point a browser at your IP on port 8080

###### SMTP Configuration

After logging in access the admin panel from the Nav Bar.
Under SMTP Servers add a new smtp server. 

If your using the local smtp server you can leave the username, password and tls values blank

If your using Gmail or some other SMTP relay fill in all the required values.

You can test the functionality of the SMTP by using the Create --> Single Email from the Nav Bar

##Usage

###### Create your first campaign.




