DOCKER_IMAGE_NAME=nginx
DOCKER_CONTAINER_NAME=web

pull-docker-image:
	# https://hub.docker.com/_/nginx/
	docker pull $(DOCKER_IMAGE_NAME)

run-server:
	# https://www.docker.com/blog/how-to-use-the-official-nginx-docker-image/
	docker run \
		-it \
		--rm \
		-d \
		-p 8080:80 \
		--name $(DOCKER_CONTAINER_NAME) \
		-v /home/x/Software/nginx/docker/site-content:/usr/share/nginx/html \
		$(DOCKER_IMAGE_NAME)

open-server:
	firefox http://localhost:8080

stop:
	docker stop $(DOCKER_CONTAINER_NAME)

run: run-server open-server

connect:
	docker exec -it $(DOCKER_CONTAINER_NAME) /bin/bash


