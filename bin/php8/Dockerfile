#Quickfix - Basebox for PHP7.2 Library now uses Debian "10" Buster, superceeding #libcurl3, stretch is most compatible at this time whilst devs workout backport.
#https://github.com/docker-library/php/issues/865

FROM php:8.0.6-apache-buster

#Surpresses debconf complaints of trying to install apt packages interactively
#https://github.com/moby/moby/issues/4032#issuecomment-192327844

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get -y update --fix-missing --no-install-recommends
RUN apt-get -y upgrade 
RUN apt-get install -y libzip-dev zip 
# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Other PHP7 Extensions

RUN docker-php-ext-install pdo 
RUN docker-php-ext-install pdo_mysql 
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install zip

# Enable apache modules
RUN a2enmod rewrite headers

ENV TZ=America/Los_Angeles
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone