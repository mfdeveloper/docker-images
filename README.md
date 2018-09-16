# Docker images

This repository contains Dockerfiles and samples to build Docker images for any languages/technologies. This images can be used to development, tests in a VPS (e.g [heroku](https://www.heroku.com/)) or automated builds/pipelines in a continuous integration.

## Images List

### PHP

 - [Wordpress Xdebug](wp-xdebug/README): The wordpress installation + [xdebug](https://xdebug.org/) support
 - [Wordpress Tools](wp-tools/README): PHP Tools for local development
 - [Wordpress CI](wp-ci/README): For local development and/or CI, containing [Wordpress installation](wp-xdebug/README) + [Wordpress Tools](wp-tools/Dockerfile)


## Docker compose

For [Docker Compose](https://docs.docker.com/compose/) example or base project, see the repositories below:

- [Wordpress Docker Compose](https://github.com/mfdeveloper/wordpress-docker-compose): A **Docker Compose** project with additional config files and scripts for automation.