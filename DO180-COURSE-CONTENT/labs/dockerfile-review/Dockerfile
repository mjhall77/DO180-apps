FROM ubi7/ubi:7.7

MAINTAINER Mike Hall mikhall@redhat.com

ENV PORT 8080

RUN yum install httpd -y && \
    yum clean all -y

RUN sed -ri -e "/^Listen 80/c\Listen ${PORT}" /etc/httpd/conf/httpd.conf && \
    chown -R apache:apache /etc/httpd/logs/ && \
    chown -R apache:apache /run/httpd/

USER apache

EXPOSE ${PORT}

COPY ./src/ /var/www/html/

CMD ["httpd", "-D", "FOREGROUND"]
