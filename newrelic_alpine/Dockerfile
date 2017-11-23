FROM alpine:3.6

MAINTAINER <tjrohweder@gmail.com>

WORKDIR /var/www

# SETTING ENVIRONMENTS - NEW_RELIC
ENV NR_INSTALL_SILENT 1
ENV NR_INSTALL_KEY a48f7c2dcc5872129ac8681568cee0014160b986

# FETCH REPOS
RUN apk update

# INSTALL AWS DEPS
RUN apk add wget gzip

# DOWNLOAD NEW_RELIC
RUN wget http://download.newrelic.com/php_agent/release/newrelic-php5-7.6.0.201-linux.tar.gz
RUN gzip -dc newrelic-php5-7.6.0.201-linux.tar.gz | tar xf -; cd newrelic-php5-7.6.0.201-linux; sh newrelic-install install



 
