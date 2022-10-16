## Introduction

Folder to learn Nginx with Docker.

## Run

First, download the Nginx Docker image:

```bash
make pull-docker-image
```

If there is a running container, stop it:

```bash
make stop
```

### Nginx as custom Docker image

```bash
make build-docker-image
make run-custom
```

### Nginx with default Docker official image

```bash
make run-official
```

## Resources

- <https://www.docker.com/blog/how-to-use-the-official-nginx-docker-image/>
