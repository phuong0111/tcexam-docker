FROM php:8.2-apache

# Install Dependencies (same as Linux, but texlive-full takes longer on Mac emulation if not native)
RUN apt-get update && apt-get install -y \
    libpng-dev libjpeg-dev libfreetype6-dev libzip-dev libxml2-dev \
    libmagickwand-dev ghostscript zbar-tools texlive-full unzip mariadb-client \
    && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd mysqli zip xml

RUN pecl install imagick && docker-php-ext-enable imagick

RUN a2enmod rewrite

WORKDIR /var/www/html

# --- KEY CHANGE: Copy from the build context root ---
COPY source_code/ .

# Copy entrypoint from the macos folder
COPY macos/entrypoint.sh /usr/local/bin/entrypoint.sh
RUN chmod +x /usr/local/bin/entrypoint.sh

RUN chown -R www-data:www-data /var/www/html && chmod -R 755 /var/www/html

EXPOSE 80
ENTRYPOINT ["entrypoint.sh"]
CMD ["apache2-foreground"]