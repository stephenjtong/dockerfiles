FROM php:8.0.6-apache-buster
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
    && php -r "if (hash_file('sha384', 'composer-setup.php') === '756890a4488ce9024fc62c56153228907f1545c228516cbf63f885e036d37e9a59d27d63f46af1d4d07ee0f76181c7d3') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer

RUN apt-get install -y libpng-dev
RUN docker-php-ext-install -j$(nproc) gd
RUN pecl install redis
RUN docker-php-ext-enable redis
RUN docker-php-ext-configure pdo_mysqli
RUN docker-php-ext-configure mysqli
RUN docker-php-ext-install -j$(nproc) mysqli
