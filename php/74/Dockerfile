FROM php:7.4-fpm

# скачка / установка пакетов
RUN apt-get update && apt-get install -y \
    	libpng-dev \
		libzip-dev \
		libxml2-dev \
    	zip \
    	libmagickwand-dev --no-install-recommends && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-install pdo pdo_mysql \
  	&& docker-php-ext-install zip \
    && docker-php-ext-install gd
    && docker-php-ext-install soap

# скачка и установка composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# скачка и установка node.js и npm
RUN curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh && bash nodesource_setup.sh && apt-get -y --allow-downgrades --allow-remove-essential --allow-change-held-packages install nodejs

# установка и включение Imagick (скачка выше)
RUN printf "\n" | pecl install imagick
RUN docker-php-ext-enable imagick

#RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"
RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"