FROM php:5.6-fpm

# 更改配置文件
ADD configFiles/www.conf /usr/local/etc/php-fpm.d/www.conf
ADD configFiles/zz-docker.conf /usr/local/etc/php-fpm.d/zz-docker.conf

# 安装扩展
RUN docker-php-ext-enable opcache \
	&& apt-get update && apt-get install -y \
	libfreetype6-dev \
	libjpeg62-turbo-dev \
	libmcrypt-dev \
	libpng-dev \
	&& docker-php-ext-install -j$(nproc) mcrypt \
	&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
	&& docker-php-ext-install -j$(nproc) gd \
	&& docker-php-ext-install -j$(nproc) mysql \
	&& docker-php-ext-install -j$(nproc) mysqli \
	&& pecl install igbinary \
	&& pecl install redis \
	&& docker-php-ext-enable igbinary \
	&& docker-php-ext-enable redis \
	&& apt-get -y install libmagickwand-dev \
	&& pecl install imagick \
	&& docker-php-ext-enable imagick
