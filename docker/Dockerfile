# syntax=docker/dockerfile:1
ARG docker_image
FROM $docker_image
# No forward logs to docker log collector.
RUN unlink /var/log/nginx/access.log
RUN unlink /var/log/nginx/error.log
# Config
COPY nginx-config/nginx.conf /etc/nginx/
COPY nginx-config/default.conf /etc/nginx/conf.d/
# SSL
RUN mkdir -p /etc/nginx/ssl
COPY nginx-config/ssl/nginx-selfsigned.crt /etc/nginx/ssl
COPY nginx-config/ssl/nginx-selfsigned.key /etc/nginx/ssl
COPY nginx-config/ssl/dhparam.pem /etc/nginx/ssl
# Basic Auth
COPY nginx-config/htpasswd/.htpasswd /etc/nginx/
