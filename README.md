maschere.it
===========

This repo contains the files from www.maschere.it

Start locally
-------------

Start apache and mysql:
```
sudo systemctl restart apache2 mysql
```

And open http://localhost:88/shop/en/


Development
-----------

Configure Apache:
Add in /etc/apache2/sites-available/001-fucina.conf
```
<VirtualHost *:88>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/public_html

        <Directory /var/www/public_html>
            AllowOverride All
            Options +Indexes
            Require all granted
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

Add a link to the previous file in /etc/apache2/sites-enabled/

Connect to local DB:
```
mysql -u cdupont -D fucina -h 127.0.0.1
```

To make a backup:
```
mysqldump -h c60429.sgvps.net -P 3306 -u <login> -p<pass> angelob6_maschere_02 > db-remote-$DATE
```
Login and password can be found on https://www.mysitearea.com/?siteId=TFE3M1luOElKZz09

Inject locally:
```
mysql -u cdupont -D fucina -h 127.0.0.1 < db-remote-$DATE
```


