FROM php:8.3-fpm

# Install required PHP extensions
RUN apt-get update && apt-get install -y \
    libicu-dev zip unzip git curl libzip-dev libonig-dev \
    && docker-php-ext-install intl pdo pdo_mysql zip mbstring opcache

# Install Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# Set working directory
WORKDIR /var/www/html

# Copy Symfony project files
COPY . /var/www/html

# Install Symfony dependencies (optional if you do it manually)
# RUN composer install

# Set permissions
RUN chown -R www-data:www-data /var/www/html
