FROM centos:latest

MAINTAINER Ravi Shankar <arsr319@gmail.com>

LABEL version="1.0" \
        release="2017-10-07"

RUN yum update -y && \
    yum install -y httpd php php-mysql mysql &&\
    yum install -y wget unzip gunzip

ENV APACHE_RUN_USER apache
ENV APACHE_RUN_GROUP apache
ENV APACHE_LOG_DIR  /var/log

RUN cd /opt && \
    wget https://wordpress.org/latest.tar.gz && \
    gunzip /opt/latest.tar.gz && \
    tar -xvf /opt/latest.tar
RUN ls -l /opt/wordpress && pwd
RUN cp -R /opt/wordpress/* /var/www/html

EXPOSE 80
#RUN systemctl enable httpd.service
ADD run-httpd.sh /run-httpd.sh
RUN chmod -v +x /run-httpd.sh

CMD ["/run-httpd.sh"]
