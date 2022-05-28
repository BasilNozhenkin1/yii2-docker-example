FROM php:5.6-fpm-alpine

RUN apt-get update && apt-get install -y \
      apt-utils \
      libmemcached-dev \
      memcached  \
      libpq-dev \
      libpng-dev \
      libzip-dev \
      libmagickwand-dev \
      zip unzip \
      git && \
      docker-php-ext-install pdo_mysql && \
      docker-php-ext-install bcmath && \
      docker-php-ext-install gd && \
      docker-php-ext-install imagick && \
      docker-php-ext-install zip && \
      docker-php-ext-enable imagick && \
      apt-get clean && \
      rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*


COPY ./_docker/app/php.ini /usr/local/etc/php/conf.d/php.ini

# Install composer
ENV COMPOSER_ALLOW_SUPERUSER=1
RUN curl -sS https://getcomposer.org/installer | php -- \
    --filename=composer \
    --install-dir=/usr/local/bin


WORKDIR /var/www