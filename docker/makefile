DOCKER_CONTAINER_NAME=web
DOCKER_CUSTOM_IMAGE_NAME=webserver
DOCKER_IMAGE_NAME=nginx:latest
DOCKER_VOLUME_LOGS=nginx-logs
DOCKER_VOLUME_WEB_CONTENT=nginx-web-content

pull-docker-image:
	# https://hub.docker.com/_/nginx/
	docker pull $(DOCKER_IMAGE_NAME)

build-docker-image:
	docker build \
	    -t $(DOCKER_CUSTOM_IMAGE_NAME) \
	    --build-arg docker_image=$(DOCKER_IMAGE_NAME) \
	    .

run-server-custom:
	docker run \
		-it \
		--rm \
		-d \
		-p 8080:80 \
		--name $(DOCKER_CONTAINER_NAME) \
		--mount type=volume,source=$(DOCKER_VOLUME_LOGS),target=/var/log/nginx \
		--mount type=volume,source=$(DOCKER_VOLUME_WEB_CONTENT),target=/usr/share/nginx/html,readonly \
		$(DOCKER_CUSTOM_IMAGE_NAME)

copy-web-content:
	/bin/bash copy-web-content-to-docker-volume $(DOCKER_VOLUME_WEB_CONTENT)

open-server:
	firefox http://localhost:8080

stop-if-running:
	docker stop $(DOCKER_CONTAINER_NAME) || true

logs:
	/bin/bash show-nginx-logs $(DOCKER_VOLUME_LOGS)

run: stop-if-running pull-docker-image build-docker-image run-server-custom copy-web-content open-server

connect:
	docker exec -it $(DOCKER_CONTAINER_NAME) /bin/bash

