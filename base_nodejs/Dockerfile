FROM centos:7

MAINTAINER <tjrohweder@gmail.com>

#Adding nginx repo
COPY ./files/nginx.repo /etc/yum.repos.d/

#Installing Epel Release REPO
RUN yum -y install epel-release 

RUN yum -y install python-pip curl nginx gcc-c++ make; pip install awscli

#Installing nodejs
RUN curl --silent --location https://rpm.nodesource.com/setup_9.x | bash -; yum -y install nodejs

#Cleaning base image
RUN yum -y remove epel-release python-pip; rm -rf /var/cache/yum; rm -rf node_modules
