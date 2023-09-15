FROM php:8.2-fpm-alpine

# env
ENV TZ=Europe/Prague
ENV WORKDIR=/var/www/becvar.app

# updates and installs system dependencies
RUN apk add --update --no-cache \
  zip \
  unzip \
  bash \
  tzdata \
  libxml2-dev \
  libpng-dev \
  libwebp-dev \
  libjpeg-turbo-dev \
  freetype-dev \
  libzip-dev \
  libxslt-dev \
  oniguruma-dev \
  linux-headers \
  $PHPIZE_DEPS && \
  rm -rf /var/cache/apk/*

# install php dependencies
RUN docker-php-ext-install -j$(nproc) gd \
  xml \
  pdo \
  pdo_mysql \
  zip 

# install composer
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

# copy php settings
COPY ./conf.d ${PHP_INI_DIR}/conf.d

# workdir
RUN mkdir -p ${WORKDIR}
WORKDIR ${WORKDIR}

# cxpose port 9000 and start php-fpm server
EXPOSE 9000

# run entrypoint
COPY ./entrypoint.sh /usr/bin/docker-entrypoint
RUN chmod +x /usr/bin/docker-entrypoint
CMD [ "docker-entrypoint" ]
