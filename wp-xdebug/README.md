# Wordpress Xdebug

A [wordpress:latest](https://github.com/docker-library/wordpress/blob/master/php7.2/apache/Dockerfile) image with **xdebug** without requirement `XDEBUG_CONFIG: remote_host` configuration

## Supported tags

- [1.0-php7.2-apache](https://github.com/mfdeveloper/docker-images/tree/1.0-php7.2-alpine)

## How to use this image

### From docker-compose

Example configuration file `docker-compose.yml`:

```yml
version: '3.3'

services:
  db:
    image: mysql
    restart: on-failure
    environment:
      MYSQL_ROOT_PASSWORD: somewordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress

  wp:
    depends_on:
    - db
    image: mfdeveloper/wordpress-xdebug
    volumes:
    - ./wp:/var/www/html
    ports:
    - 8080:80
    restart: on-failure
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
```
