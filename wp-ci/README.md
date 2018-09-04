# Wordpress CI

A [wordpress image](https://hub.docker.com/_/wordpress/) + [php tools](../wp-tools/Dockerfile) to run plugin configs and phpunit tests, in a CI or local development/tests (e.g circleci, travis, gitlabci ...)

## Supported tags

- [latest](https://github.com/mfdeveloper/docker-images/tree/latest)

## Tools


 - [PHP 7.2](https://hub.docker.com/_/php/)
 - [Composer](https://getcomposer.org/)
 - [PHPUnit](https://phpunit.de/)
 - [PHPCS](https://github.com/squizlabs/PHP_CodeSniffer)
 - [Wordpress Coding Standards](https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards)
 - [Wordpress Cli](https://wp-cli.org/)

## How to use this image

### From aliases

Create a shell script alias for each tool in this image, like this:

**file /bin/sh/composer.sh**
```bash
#!/bin/sh

tty=
tty -s && tty=--tty
docker run \
       $tty \
       -i \
       --rm \
       --network=host \
       -v "$HOME":"$HOME":ro \
       -u $(id -u) \
       -w "$PWD" \
       mfdeveloper/wordpress-ci:latest composer "$@"

exit $?
```

An run:

```bash
./composer.sh [any-action-here]
```
### From docker (directly)

Just execute the tool using `docker run`:

```bash
docker run --rm -i mfdeveloper/wordpress-ci composer [any-action-here]
```

### From docker-compose

**docker-compose.yml**

```yml
 version: '3.1'
 services:
    wordpress:
        image: wordpress
        volumes:
            - wp-code:/var/www/html
            - ./wp-content:/var/www/html/wp-content
    wp-tools:
        image: mfdeveloper/wordpress-ci
        depends_on:
            - wordpress
        volumes:
            # Share the same volumes with 
            # "wordpress" service
            - wp-code:/var/www/html
            - ./wp-content:/var/www/html/wp-content
            - .:/app
volumes:
   wp-code:
```
