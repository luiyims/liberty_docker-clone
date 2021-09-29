FROM php:7.3-fpm

COPY conf /usr/local/etc/php

RUN apt-get update
RUN apt-get install -y libfreetype6-dev
RUN apt-get install -y libjpeg62-turbo-dev
RUN apt-get install -y libpng-dev
RUN apt-get install -y git
RUN apt-get install -y libzip-dev libz-dev libmemcached-dev libmemcached11 libmemcachedutil2 build-essential memcached
RUN docker-php-ext-install -j$(nproc) iconv
RUN docker-php-ext-install -j$(nproc) gd
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install -j$(nproc) mysqli
RUN docker-php-ext-install -j$(nproc) pdo_mysql
RUN docker-php-ext-install -j$(nproc) zip
RUN docker-php-ext-install -j$(nproc) opcache
RUN pecl install memcached
RUN echo extension=memcached.so >> /usr/local/etc/php/conf.d/memcached.ini

RUN curl -sL https://deb.nodesource.com/setup_8.x | apt-get install -y nodejs

#OLD REPO WORKDIR
#WORKDIR /usr/share/apache2/htdocs/flowbusiness_co
WORKDIR /usr/share/apache2/htdocs/flow-business

COPY --from=composer:1 /usr/bin/composer /usr/bin/composer

#CMD  ln -s /usr/share/apache2/htdocs/flow-business/web /usr/share/apache2/htdocs/flow-business/web/jamaica