FROM php:5.4-fpm

# скачка / установка пакетов
RUN apt-get update && apt-get install -y \
    	libpng-dev \
		libzip-dev \
		libxml2-dev \
    	zip \
#    	wget \
    	libmagickwand-dev --no-install-recommends && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-install pdo pdo_mysql \
  	&& docker-php-ext-install zip \
    && docker-php-ext-install gd \
    && docker-php-ext-install mbstring \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install soap

# скачка и установка composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

#RUN apt-get install -y \ lzip \ xz-lzma

RUN apt-get update && apt-get install -y ca-certificates

# скачка и установка node.js и npm
RUN curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh \
#    && bash nodesource_setup.sh \
#    && apt-get -y --force-yes install nodejs

#RUN curl -sL https://deb.nodesource.com/setup_12.x | sed 's|https://|http://|' | bash - && apt-get install -y nodejs

# можно попробовать это, но нужно ставить wget и tar
#RUN \
#	mkdir -p /usr/local/src && \
#	chown ${MY_USER}:${MY_GROUP} /usr/local/src && \
#	VERSION="$( curl -Lq https://nodejs.org 2>/dev/null | grep LTS | grep -Eo 'data-version.*.' | grep -oE 'v[0-9.]+' )" && \
#	wget -P /usr/local/src https://nodejs.org/dist/${VERSION}/node-${VERSION}-linux-x64.tar.xz && \
#	tar xvf /usr/local/src/node-${VERSION}-linux-x64.tar.xz -C /usr/local/src && \
#	ln -s /usr/local/src/node-${VERSION}-linux-x64 /usr/local/node && \
#	ln -s /usr/local/node/bin/* /usr/local/bin/ && \
#	rm -f /usr/local/src/node-${VERSION}-linux-x64.tar.xz

# установка и включение Imagick (скачка выше)
RUN printf "\n" | pecl install imagick
RUN docker-php-ext-enable imagick

#RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"
#RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"