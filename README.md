# PHP
PHP Dockerfiles with additional libraries (mainly for our needs)

## Example of Usage

Move to the folder containing the desired Dockerfile.

Build the image
```
docker build -t <dockertag> .
```

Create a shell script called `php<version>.sh` with this content :
```
#!/bin/bash
docker run --rm --interactive --tty \
  --workdir /usr/src/myapp \
  --volume $PWD:/usr/src/myapp \
  --user $(id -u):$(id -g) \
  <dockertag> php "$@"
```

## Dockerhub
All images are available at : https://hub.docker.com/r/ihneo/php

You can pull all images with the command :
```
docker pull ihneo/php:<dockertag>
```

## Supported tags and respective `Dockerfile` links

-	[`7.1-cli-alpine`](https://github.com/ihneo/php/blob/master/7.1/alpine/cli/Dockerfile)
-	[`7.2-cli-alpine`](https://github.com/ihneo/php/blob/master/7.2/alpine/cli/Dockerfile)
-	[`7.3-cli-alpine`](https://github.com/ihneo/php/blob/master/7.3/alpine/cli/Dockerfile)
-	[`7.4-cli-alpine`](https://github.com/ihneo/php/blob/master/7.4/alpine/cli/Dockerfile)
-	[`8.0-cli-alpine`](https://github.com/ihneo/php/blob/master/8.0/alpine/cli/Dockerfile)
-	[`8.1-cli-alpine`](https://github.com/ihneo/php/blob/master/8.1/alpine/cli/Dockerfile)
-	[`8.2-cli-alpine`](https://github.com/ihneo/php/blob/master/8.2/alpine/cli/Dockerfile)
-	[`8.3-cli-alpine`](https://github.com/ihneo/php/blob/master/8.3/alpine/cli/Dockerfile)
-	[`8.4-cli-alpine`, `latest`](https://github.com/ihneo/php/blob/master/8.4/alpine/cli/Dockerfile)
-	[`7.1-fpm-alpine`](https://github.com/ihneo/php/blob/master/7.1/alpine/fpm/Dockerfile)
-	[`7.2-fpm-alpine`](https://github.com/ihneo/php/blob/master/7.2/alpine/fpm/Dockerfile)
-	[`7.3-fpm-alpine`](https://github.com/ihneo/php/blob/master/7.3/alpine/fpm/Dockerfile)
-	[`7.4-fpm-alpine`](https://github.com/ihneo/php/blob/master/7.4/alpine/fpm/Dockerfile)
-	[`8.0-fpm-alpine`](https://github.com/ihneo/php/blob/master/8.0/alpine/fpm/Dockerfile)
-	[`8.1-fpm-alpine`](https://github.com/ihneo/php/blob/master/8.1/alpine/fpm/Dockerfile)
-	[`8.2-fpm-alpine`](https://github.com/ihneo/php/blob/master/8.2/alpine/fpm/Dockerfile)
-	[`8.3-fpm-alpine`](https://github.com/ihneo/php/blob/master/8.3/alpine/fpm/Dockerfile)
-	[`8.4-fpm-alpine`](https://github.com/ihneo/php/blob/master/8.4/alpine/fpm/Dockerfile)

## Example of usage with the images available at Dockerhub
```
#!/bin/bash
docker run --rm --interactive --tty \
  --workdir /usr/src/myapp \
  --volume $PWD:/usr/src/myapp \
  --user $(id -u):$(id -g) \
  ihneo/php:<dockertag> php "$@"
```

## Composer
Composer is also available in all images

To use composer in version 1, command is `composer`

To use composer in version 2, command is `composer2`

An example to use the docker image as a composer binary :
```
#!/bin/bash
docker run --rm --interactive --tty \
  --env COMPOSER_HOME=/tmp/composer/config \
  --env COMPOSER_CACHE_DIR=/tmp/composer/cache \
  --workdir /app \
  --volume $PWD:/app \
  --volume ${COMPOSER_HOME:-$HOME/.config/composer}:/tmp/composer/config \
  --volume ${COMPOSER_CACHE_DIR:-$HOME/.cache/composer}:/tmp/composer/cache \
  --user $(id -u):$(id -g) \
  ihneo/php:<dockertag> composer "$@"
```