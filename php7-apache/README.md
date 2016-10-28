# php7-apache

A Docker image for Apache and PHP 7.0 based on Fedora 22.

This container use the [PHP 7.0 from Rémi](https://blog.remirepo.net/post/2016/02/14/Install-PHP-7-on-CentOS-RHEL-Fedora).


## Build the image: 

```
# cd php7-apache
# docker build -t phpguru/php7-apache .
```

## Start

### Background
To start a container in the background accessible on localhost:8000

```
# docker run -d -p 8000:80 phpguru/php7-apache
```

### Mount your files
The virtualhost.conf file expose the /src directory. As a default, it only contains an index.php file with a phpinfo(). You can use a volume to overrides this directory:

```
# docker run -d -v /your/php/directory:/src -p 8000:80 phpguru/php7-apache
```

### PHP CLI
To start a container with an interactive shell 

```
# docker run -it -p 8000:80 phpguru/php7-apache /bin/bash
```

From their, you can use PHP 7 cli

```
# php -v
```

or enable the PHP 7 SCL to use the standard command

```
# source /opt/remi/php70/enable
# php -v
```

You can also start apache with:

```
# /run-apache.sh
```

After that, use `apachectl -k [stop|start|restart]`

