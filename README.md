## Installation

```
sudo apt-get update
sudo apt-get install apache2 apache2-utils libexpat1 ssl-cert python
sudo apt-get install libapache2-mod-wsgi

# we may need to install only the py3 version of the package
sudo apt-get install libapache2-mod-wsgi-py3
sudo systemctl restart apache2
```

Draft a config:

```
sudo vi /etc/apache2/conf-available/mod-wsgi.conf
```

And put this line in it:

```
WSGIScriptAlias /test_wsgi /var/www/html/test_script.py
```

Enable the config:

```
sudo a2enconf mod-wsgi
sudo systemctl restart apache2
```
