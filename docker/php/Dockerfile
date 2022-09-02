FROM php:8.1-fpm

RUN apt update \
    && apt install -y \
      g++ \
      joe \
      less \
      zip \
      libicu-dev \
      libbz2-dev \
      libldap2-dev \
      libpng-dev \
      libpq-dev \
      librabbitmq-dev \
      libzip-dev \
      libtidy-dev \
      libxslt-dev \
      zlib1g-dev \
    && docker-php-ext-install bcmath bz2 \
      calendar exif \
      gd gettext \
      ldap pcntl \
      intl opcache \
      pdo pdo_mysql pdo_pgsql \
      sysvmsg sysvsem sysvshm \
      tidy \
      xsl zip \
    && pecl install amqp \
    && docker-php-ext-enable amqp \
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && echo "xdebug.mode=debug" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.client_host=host.docker.internal" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.idekey=PHPSTORM" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

COPY root/.bashrc /root

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony5/bin/symfony /usr/local/bin/symfony

WORKDIR /var/www/api
