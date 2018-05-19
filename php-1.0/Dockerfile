FROM php:7.2-apache

COPY vhost.conf /etc/apache2/sites-available/000-default.conf
COPY php.ini /usr/local/etc/php/

RUN apt-get update && apt-get install -y wget libxml2-dev libzip-dev \
  && docker-php-ext-install -j$(nproc) mbstring pdo pdo_mysql zip soap json dom

ADD composer_installer.sh /usr/local/bin/composer_installer.sh
RUN /usr/local/bin/composer_installer.sh

COPY . /var/www/html/
WORKDIR /var/www/html/

RUN a2enmod rewrite
