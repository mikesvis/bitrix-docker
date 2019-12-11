FROM php:7.3-apache
RUN apt-get update && apt-get upgrade -y \
    && apt-get install -y libpng-dev libzip-dev libfreetype6-dev libjpeg62-turbo-dev \
    && docker-php-ext-configure gd --with-freetype-dir --with-jpeg-dir \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install mysqli zip \
    && echo "date.timezone = Europe/Moscow" > /usr/local/etc/php/php.ini \
    && echo "mbstring.func_overload = 2" > /usr/local/etc/php/php.ini \
    && echo "mbstring.internal_encoding = 'utf-8'" > /usr/local/etc/php/php.ini \
    && sed -i "/short_open_tag = .*/c\short_open_tag = On" /usr/local/etc/php/php.ini \
    && sed -i "/max_input_vars = .*/c\max_input_vars = 10000" /usr/local/etc/php/php.ini 
EXPOSE 80
