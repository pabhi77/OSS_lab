FROM php:7.4-apache

RUN apt-get update \
    && apt-get install -y \
        libpng-dev \
        libjpeg-dev \
        libfreetype6-dev \
        libzip-dev \
        mariadb-client \
        unzip \
        wget \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd mysqli pdo_mysql zip \
    && a2enmod rewrite

WORKDIR /var/www/html

RUN wget https://www.mantisbt.org/download.php --no-check-certificate \
    && unzip download.php \
    && mv mantisbt-*/* . \
    && rm -r download.php mantisbt-*

COPY config_inc.php /var/www/html/config/config_inc.php
