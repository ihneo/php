FROM php:8.0-cli-alpine

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
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip

# exif
RUN apk add --update --no-cache exiftool \
    && docker-php-ext-install exif

# imagick
#RUN apk add --update --no-cache build-base autoconf imagemagick imagemagick-dev \
#    && pecl install imagick \
#    && docker-php-ext-enable imagick

#RUN apk add --update --no-cache autoconf g++ imagemagick-dev libtool make pcre-dev \
#    && pecl install imagick \
#    && docker-php-ext-enable imagick \
#    && apk del autoconf g++ libtool make pcre-dev

# intl
RUN apk add --update --no-cache icu-dev \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl

# gd
RUN apk add --update --no-cache libpng-dev \
    && docker-php-ext-configure gd \
    && docker-php-ext-install gd

