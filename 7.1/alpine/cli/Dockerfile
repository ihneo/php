FROM php:7.1-cli-alpine

# bash
RUN apk add --update --no-cache bash

# gmp
RUN apk add --update --no-cache gmp-dev \
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

# intl
RUN apk add --update --no-cache icu-dev \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl

# gd
RUN apk add --update --no-cache libpng-dev \
    && docker-php-ext-configure gd \
    && docker-php-ext-install gd

# git client
RUN apk add --update --no-cache git

# composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --1 --filename=composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --2 --filename=composer2
