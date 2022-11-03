DOCKER_IMAGE_NAME=nginx
DOCKER_CUSTOM_IMAGE_NAME=webserver
DOCKER_CONTAINER_NAME=web
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
		--mount source=nginx-vol,target=/var/log/nginx \
		$(DOCKER_CUSTOM_IMAGE_NAME)

run-server-official:
	docker run \
		-it \
		--rm \
		-d \
		-p 8080:80 \
		--name $(DOCKER_CONTAINER_NAME) \
		--mount type=bind,source=$(ROOT_DIR)/site-content,target=/usr/share/nginx/html,readonly \
		$(DOCKER_IMAGE_NAME)

open-server:
	firefox http://localhost:8080

stop:
	docker stop $(DOCKER_CONTAINER_NAME)

run-official: run-server-official open-server

run-custom: run-server-custom open-server

connect:
	docker exec -it $(DOCKER_CONTAINER_NAME) /bin/bash

