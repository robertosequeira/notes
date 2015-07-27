# NGINX

* Start, restart, stop server
```
sudo /etc/init.d/nginx start
sudo /etc/init.d/nginx stop
sudo /etc/init.d/nginx restart

or

sudo service nginx start
sudo service nginx restart
sudo service nginx stop
```

* Load changes 
```
sudo nginx -s reload
```

* Add a new site

```
$ cd /etc/nginx/sites-available
... create newproject.com ...

$ cd /etc/nginx/sites-enabled
$ ln -s ../sites-available/newproject.com .

$ /etc/init.d/nginx reload
[....] Reloading nginx configuration: nginx.
$
```

* Verify config files syntax
```
sudo nginx -t
```
