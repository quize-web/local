FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
    	libpng-dev \
		libzip-dev \
    	zip \
    && docker-php-ext-install pdo pdo_mysql \
  	&& docker-php-ext-install zip \
    && docker-php-ext-install gd

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh && bash nodesource_setup.sh && apt-get -y --allow-downgrades --allow-remove-essential --allow-change-held-packages install nodejs

#RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"
RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"