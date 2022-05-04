FROM php:7.4-fpm

RUN apt-get update && apt-get install -y --no-install-recommends \
  libpq-dev \
  libzip-dev \
  default-mysql-client \
  python3 \
  unzip \
  && docker-php-ext-install \
  pdo_mysql \
  sockets \
  zip \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

COPY --from=composer:1 /usr/bin/composer /usr/bin/composer

COPY --from=node:16.15 /usr/local/bin /usr/local/bin
COPY --from=node:16.15 /usr/local/lib /usr/local/lib

WORKDIR /var/www/html
