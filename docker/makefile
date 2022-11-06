DOCKER_IMAGE_NAME=nginx
DOCKER_CUSTOM_IMAGE_NAME=webserver
DOCKER_CONTAINER_NAME=web
DOCKER_VOLUME=nginx-vol
ROOT_DIR:=$(shell dirname $(realpath $(firstword $(MAKEFILE_LIST))))

pull-docker-image:
	# https://hub.docker.com/_/nginx/
	docker pull $(DOCKER_IMAGE_NAME)

build-docker-image:
	docker build -t $(DOCKER_CUSTOM_IMAGE_NAME) .

run-server-custom:
	docker run \
		-it \
		--rm \
		-d \
		-p 8080:80 \
		--name $(DOCKER_CONTAINER_NAME) \
		--mount type=volume,source=$(DOCKER_VOLUME),target=/var/log/nginx \
		--mount type=volume,source=nginx-content,target=/usr/share/nginx/html,readonly \
		$(DOCKER_CUSTOM_IMAGE_NAME)

copy-web-content:
	/bin/bash copy-web-content-to-docker-volume

open-server:
	firefox http://localhost:8080

stop:
	docker stop $(DOCKER_CONTAINER_NAME)

logs:
	sudo tail -f /var/lib/docker/volumes/$(DOCKER_VOLUME)/_data/access.log

run-custom: run-server-custom copy-web-content open-server

connect:
	docker exec -it $(DOCKER_CONTAINER_NAME) /bin/bash

