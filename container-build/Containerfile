# Use the httpd-parent image as base
FROM quay.io/redhattraining/httpd-parent

LABEL io.k8s.description="A Basic image apache server" \
      io.k8s.display-name="Apache httpd server" \
      io.openshift.expose-services="8080:http" \
      io.openshift.tag="apache,httpd"

RUN sed -i "s/Listen 80/Listen 8080/g" /etc/httpd/conf/httpd.conf && \
    sed -i "s/#ServerName www.example.com:80/ServerName 0.0.0.0:8080/g" /etc/httpd/conf/httpd.conf && \
    chgrp -R 0 /var/log/httpd /var/run/httpd && \
    chmod -R g=u /var/log/httpd /var/run/httpd

ONBUILD COPY src/ /var/www/html/

EXPOSE 8080

USER 1001

CMD /usr/sbin/httpd -DFOREGROUND
