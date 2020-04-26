FROM php:7.4-cli-alpine

# gmp
RUN apk add --update --no-cache gmp gmp-dev \
    && docker-php-ext-install gmp

# mysqli, pdo, pdo_mysql, pdo_pgsql
RUN apk add --update --no-cache postgresql-dev \
    && docker-php-ext-install mysqli pdo pdo_mysql

# zip
RUN apk add --update --no-cache libzip-dev \
    && docker-php-ext-configure zip --with-libzip=/usr/include \
    && docker-php-ext-install zip

# exif
RUN apk add --update --no-cache exiftool \
    && docker-php-ext-install exif

# imagick
RUN apk add --update --no-cache build-base imagemagick-dev php7-pecl-imagick autoconf \
    && echo "" | pecl install imagick \
    && echo "extension=imagick.so" > /usr/local/etc/php/conf.d/docker-php-ext-imagick.ini

