FROM httpd:2.4-alpine

ENV TZ=Europe/Prague
ENV SERVER_NAME=localhost
ENV APP_ROOT=/var/www/becvar.app
ENV DOCUMENT_ROOT=${APP_ROOT}/www/public
ENV APACHE_LOG_DIR=${APP_ROOT}/services/apache/logs
ENV APACHE_RUN_USER=www-data
ENV APACHE_RUN_GROUP=www-data

RUN apk add --update --no-cache tzdata

WORKDIR ${APP_ROOT}

RUN mkdir -p ${APP_ROOT}
RUN mkdir -p ${DOCUMENT_ROOT}

RUN chown -R ${APACHE_RUN_USER}:${APACHE_RUN_USER} ${APP_ROOT}
RUN chown -R ${APACHE_RUN_USER}:${APACHE_RUN_USER} ${DOCUMENT_ROOT}

RUN ln -s ${APP_ROOT}/www/public/index.php ${DOCUMENT_ROOT}

COPY ./httpd.conf /usr/local/apache2/conf/httpd.conf
