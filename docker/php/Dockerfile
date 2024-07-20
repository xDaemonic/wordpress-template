FROM php:8.2-fpm

# Install dependencies
RUN apt-get update && apt-get install -y \
    libmagickwand-dev \
    libcurl4-openssl-dev \
    libxml2 \
    libicu-dev \
    libonig-dev \
    libpng-dev \
    openssl \
    libssh-dev \
    libzip-dev \
    libmemcached-dev \
    libgd-dev \
    zlib1g \
    libz-dev \
    libzip-dev \
    libc6-dev \
    libfreetype6-dev \
    libjpeg-dev \
    libwebp-dev \
    libssh2-1-dev  \
    wget \
    curl

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install pecl packages
RUN pecl install igbinary imagick redis timezonedb apcu memcached openssl ssh2

# Configure extensions
RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-configure mysqli --with-mysqli=mysqlnd
RUN docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd

# Install extensions
RUN docker-php-ext-install gd \
	zip \
	xml \
	exif \
	curl \
	intl \
	mbstring \
	bcmath \
	filter \
	iconv \
	shmop \
	simplexml \
	ftp \
	sockets \
	pdo \
	pdo_mysql  \
	mysqli

# Enable extensions
RUN docker-php-ext-enable imagick igbinary redis memcached apcu opcache timezonedb ssh2
