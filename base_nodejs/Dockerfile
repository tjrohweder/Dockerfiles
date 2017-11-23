FROM centos:7

WORKDIR /var/www

MAINTAINER <tjrohweder@gmail.com>

#Adding nginx repo
COPY ./files/nginx.repo /etc/yum.repos.d/

#Installing Epel Release REPO
RUN yum -y install epel-release 

RUN yum -y install curl nginx gcc-c++ make

#Installing nodejs
RUN curl --silent --location https://rpm.nodesource.com/setup_9.x | bash -; yum -y install nodejs

#Cleaning base image
RUN yum -y remove epel-release python-pip; rm -rf /var/cache/yum; rm -rf node_modules

# COPY NGINX CONFIGS
RUN rm -rf /etc/nginx; mkdir -p /run/nginx
COPY ./docker_conf/nginx /etc/nginx

ADD . .

RUN mkdir -p /var/www/hml
RUN mkdir -p /var/www/prd

RUN npm install

RUN ./node_modules/.bin/ng build --prod --env=hom --bh /ecred/ --aot=false
RUN mv dist /var/www/hml/ecred

RUN ./node_modules/.bin/ng build --prod --bh /ecred/ --aot=false
RUN mv dist /var/www/prd/ecred

RUN rm -rf .angular-cli.json CHANGELOG.md DEV.md Dockerfile Dockerfile02 README.md build.sh dist.sh dist_dev.zip dist_hml.zip dist_prd.zip dist_prd_old.zip \
docker_conf e2e karma.conf.js package-lock.json package.json protractor.conf.js tsconfig.json tslint.json node_modules src; yum -y remove gcc-c++ make curl; rm -rf /var/cache/yum

ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]

