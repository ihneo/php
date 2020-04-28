# PHP
PHP Dockerfiles with additional libraries (mainly for our needs)

## Example of Usage

Move to the folder containing the desired Dockerfile.

Build the image
```
docker build -t <dockertag> .
```

Create a shell script called `php7<version>.sh` with this content :
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
-	[`7.3-cli-alpine`](https://github.com/ihneo/php/blob/master/7.3/alpine/cli/Dockerfile)
-	[`7.4-cli-alpine`](https://github.com/ihneo/php/blob/master/7.4/alpine/cli/Dockerfile)

## Example of usage with the images available at Dockerhub
```
#!/bin/bash
docker run --rm --interactive --tty \
  --workdir /usr/src/myapp \
  --volume $PWD:/usr/src/myapp \
  --user $(id -u):$(id -g) \
  ihneo/php:<dockertag> php "$@"
```