FROM alpine:3.7

WORKDIR /var/www

# SETTING ENVIRONMENTS - NEW_RELIC
ENV ENVIRONMENT dev
ENV NR_INSTALL_SILENT true
ENV NR_INSTALL_KEY <your-key>

# FETCH REPOS
RUN apk add --no-cache wget gzip


# INSTALLING NEW_RELIC
RUN mkdir /opt && cd /opt; \
         wget https://download.newrelic.com/php_agent/release/newrelic-php5-7.6.0.201-linux-musl.tar.gz --no-check-certificate; \
         tar -xzvf newrelic-php5-7.6.0.201-linux-musl.tar.gz; \
         ./newrelic-php5-7.6.0.201-linux-musl/newrelic-install install; \
         sed -i 's/newrelic.appname = "App Name"/newrelic.appname = "PIM '${ENVIRONMENT}'"/g' /etc/php7/conf.d/newrelic.ini

# CLEANING IMAGE
RUN apk del wget gzip; rm -rf newrelic-php5-7.6.0.201-linux.tar.gz /var/cache/apk
