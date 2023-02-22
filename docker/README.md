## Introduction

Folder to learn Nginx with Docker.

## Configuration

Generate the required files for SSL:

```bash
cd nginx-config/ssl/
./generate-files
# You can answer the questions with the default options.
```

Generate the required files for authentication:

```bash
cd nginx-config/htpasswd/
./generate-files
```

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

## Logs

```bash
make logs
```

## Resources

- Create image: <https://www.docker.com/blog/how-to-use-the-official-nginx-docker-image/>
- Configure the server (logs, content, etc.): <https://www.nginx.com/blog/deploying-nginx-nginx-plus-docker/#more-info>
- Configure logs output: <https://notestack.io/public/configure-nginx-logging-in-a-docker-container/874f1253-cf1a-4c62-9d2d-467ab23c258d>
