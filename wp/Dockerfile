FROM sdpfoue/php8-xhprof
RUN docker-php-ext-configure mysqli
RUN docker-php-ext-install -j$(nproc) mysqli
