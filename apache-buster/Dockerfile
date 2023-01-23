# base image
FROM php:8.2-apache-buster

# setting operating system
RUN apt-get update \
  && apt-get install -y libicu-dev libzip-dev libpng-dev libjpeg62-turbo-dev git wget acl ffmpeg --no-install-recommends \
  # refs. https://mongoc.org/libmongoc/current/installing.html
  libbson-1.0-0 cmake libssl-dev libsasl2-dev \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# setting middleware
RUN pecl install grpc
RUN docker-php-ext-install zip
RUN docker-php-ext-configure gd --with-jpeg=/usr/include/
RUN docker-php-ext-install gd
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-enable grpc
RUN docker-php-ext-install intl
RUN pecl install mongodb \
    && docker-php-ext-enable mongodb

