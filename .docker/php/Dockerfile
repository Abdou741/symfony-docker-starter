FROM node:latest AS node
FROM php:8.1.7-fpm

LABEL Maintainer="Yahya Hindioglu <business@yahyahindioglu.com>" \
      Description="Symfony PHP docker file."

RUN apt-get update && apt-get install -y \
    gnupg \
    g++ \
    procps \
    openssl \
    git \
    unzip \
    zlib1g-dev \
    libzip-dev \
    libfreetype6-dev \
    libpng-dev \
    libjpeg-dev \
    libpq-dev \
    libicu-dev  \
    libonig-dev \
    libxslt1-dev \
    acl \
    && echo 'alias sf="php bin/console"' >> ~/.bashrc

COPY --from=node /usr/local/lib/node_modules /usr/local/lib/node_modules
COPY --from=node /usr/local/bin/node /usr/local/bin/node
RUN ln -s /usr/local/lib/node_modules/npm/bin/npm-cli.js /usr/local/bin/npm

RUN docker-php-ext-configure gd --with-jpeg --with-freetype

RUN pecl install xdebug apcu
RUN docker-php-ext-enable apcu xdebug

RUN docker-php-ext-install \
    pgsql pdo_pgsql zip xsl gd intl opcache exif mbstring

WORKDIR /var/www/symfony_docker

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony
RUN alias composer='php /usr/local/bin/composer'

CMD bash -c "composer install --ignore-platform-reqs"
