# syntax=docker/dockerfile:1
ARG docker_image
FROM $docker_image
# No forward logs to docker log collector.
RUN unlink /var/log/nginx/access.log
RUN unlink /var/log/nginx/error.log
