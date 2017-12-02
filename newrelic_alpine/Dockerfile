FROM alpine:3.6

MAINTAINER <tjrohweder@gmail.com>

WORKDIR /var/www

# SETTING ENVIRONMENTS - NEW_RELIC
ENV NR_INSTALL_SILENT 1
ENV NR_INSTALL_KEY <your-key>

# FETCH REPOS
RUN apk add --no-cache wget gzip

# DOWNLOAD NEW_RELIC
RUN wget http://download.newrelic.com/php_agent/release/newrelic-php5-7.6.0.201-linux.tar.gz
RUN gzip -dc newrelic-php5-7.6.0.201-linux.tar.gz | tar xf -; cd newrelic-php5-7.6.0.201-linux; sh newrelic-install install

# CLEANING IMAGE
RUN apk del wget gzip; rm -rf newrelic-php5-7.6.0.201-linux.tar.gz /var/cache/apk
