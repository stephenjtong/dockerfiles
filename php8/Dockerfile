FROM php:apache-buster
RUN a2enmod ssl
RUN a2enmod rewrite
RUN apt-get update
RUN apt-get install -y libldap-dev libzip-dev
RUN docker-php-ext-configure ldap
RUN docker-php-ext-install -j$(nproc) ldap
RUN docker-php-ext-configure pdo_mysql
RUN docker-php-ext-install -j$(nproc) pdo_mysql
RUN docker-php-ext-configure zip
RUN docker-php-ext-install -j$(nproc) zip

RUN pecl install xhprof
RUN docker-php-ext-enable xhprof

RUN pecl install mongodb
RUN docker-php-ext-enable mongodb

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer

RUN apt-get install -y libpng-dev
RUN docker-php-ext-install -j$(nproc) gd
RUN pecl install redis
RUN docker-php-ext-enable redis
RUN docker-php-ext-configure pdo_mysql
RUN docker-php-ext-configure mysqli
RUN docker-php-ext-install -j$(nproc) mysqli
