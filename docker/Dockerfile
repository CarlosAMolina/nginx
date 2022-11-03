FROM nginx:latest
# No forward logs to docker log collector.
RUN unlink /var/log/nginx/access.log
RUN unlink /var/log/nginx/error.log
# Copy web contents.
COPY ./site-content/index.html /usr/share/nginx/html/index.html
