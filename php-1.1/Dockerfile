FROM php:7.2-apache

COPY php.ini /usr/local/etc/php/
COPY composer_installer.sh /usr/local/bin/composer_installer.sh
COPY vhost.conf /etc/apache2/sites-available/000-default.conf

RUN apt-get update && apt-get install -y wget openssh-client libxml2-dev libzip-dev \
  && docker-php-ext-install -j$(nproc) mbstring pdo pdo_mysql zip soap json dom

RUN /usr/local/bin/composer_installer.sh
RUN a2enmod rewrite

COPY . /var/www/html/
WORKDIR /var/www/html/
