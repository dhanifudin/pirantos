FROM php:7.3-alpine

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN apk add --no-cache git tini icu-dev postgresql-dev libpng-dev oniguruma-dev \
	&& docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
	&& docker-php-ext-install pdo pdo_pgsql mbstring exif pcntl bcmath gd intl

COPY docker-entrypoint.sh /docker-entrypoint.sh

WORKDIR /app

ENTRYPOINT ["/docker-entrypoint.sh"]

CMD ["composer"]
