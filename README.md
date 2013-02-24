Install Ubuntu 12.04 server
===========================

Install lamp phpmyadmin git
---------------------------
sudo sudo apt-get update

sudo apt-get install lamp-server^

sudo apt-get install phpmyadmin

sudo apt-get install git


Enable mod-rewrite (zend)
-------------------------
sudo a2enmod rewrite

Enable php errors
-----------------
sudo nano /etc/php5/apache2/php.ini 

find this line and change:
	
	display_errors = On

Restart server
--------------
sudo service apache2 restart

Clone repository
----------------
cd /var/www

sudo git clone https://github.com/emersonmatsumoto/zendalbum.git


Install zend framework
----------------------
sudo php composer.phar self-update

sudo php composer.phar install


Create database
===============

http://localhost/phpmyadmin

->Databases

->Create new database:
	
	zf2tutorial

Reload navigation frame and click zf2tutorial

click SQL and paste:


	CREATE TABLE album (
	  id int(11) NOT NULL auto_increment,
	  artist varchar(100) NOT NULL,
	  title varchar(100) NOT NULL,
	  PRIMARY KEY (id)
	);
	INSERT INTO album (artist, title)
		VALUES  ('The  Military  Wives',  'In  My  Dreams');
	INSERT INTO album (artist, title)
		VALUES  ('Adele',  '21');
	INSERT INTO album (artist, title)
		VALUES  ('Bruce  Springsteen',  'Wrecking Ball (Deluxe)');
	INSERT INTO album (artist, title)
		VALUES  ('Lana  Del  Rey',  'Born  To  Die');
	INSERT INTO album (artist, title)
		VALUES  ('Gotye',  'Making  Mirrors');

Edit global.php
===============

/var/www/zendalbum/config/autoload/global.php


ZendSkeletonApplication
=======================

Introduction
------------
This is a simple, skeleton application using the ZF2 MVC layer and module
systems. This application is meant to be used as a starting place for those
looking to get their feet wet with ZF2.


Installation
------------

Using Composer (recommended)
----------------------------
The recommended way to get a working copy of this project is to clone the repository
and use `composer` to install dependencies using the `create-project` command:

    curl -s https://getcomposer.org/installer | php --
    php composer.phar create-project --repository-url="http://packages.zendframework.com" zendframework/skeleton-application path/to/install

Alternately, clone the repository and manually invoke `composer` using the shipped
`composer.phar`:

    cd my/project/dir
    git clone git://github.com/zendframework/ZendSkeletonApplication.git
    cd ZendSkeletonApplication
    php composer.phar self-update
    php composer.phar install

(The `self-update` directive is to ensure you have an up-to-date `composer.phar`
available.)

Another alternative for downloading the project is to grab it via `curl`, and
then pass it to `tar`:

    cd my/project/dir
    curl -#L https://github.com/zendframework/ZendSkeletonApplication/tarball/master | tar xz --strip-components=1

You would then invoke `composer` to install dependencies per the previous
example.

Using Git submodules
--------------------
Alternatively, you can install using native git submodules:

    git clone git://github.com/zendframework/ZendSkeletonApplication.git --recursive

Virtual Host
------------
Afterwards, set up a virtual host to point to the public/ directory of the
project and you should be ready to go!
