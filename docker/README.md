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

### API

In this section, we will see an example of how to use an API behind Nginx.

You can get an API executable from <https://github.com/CarlosAMolina/rust/tree/master/warp/hello-world>, the file name is `hello-world`.

To run the following steps, the Nginx Docker container must be running.

Copy the executable to the container:

```bash
docker cp hello-world web:/tmp/
make connect
./tmp/hello-world
```

In other terminal window, call the API:

```bash
make get-api-call
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

Access logs:

```bash
make logs
```

Error logs:

```bash
make logs-error
```

## How to check the Nginx configuration

Once the server is running, you can check the configuration by sending requests or visiting different URLs.

### Frame

Open in your web browser the following file:

```bash
firefox web-pages-for-testing/frame.html
```

## Resources

- API: <https://serverfault.com/questions/801725/nginx-config-for-restful-api-behind-proxy>
- Create image: <https://www.docker.com/blog/how-to-use-the-official-nginx-docker-image/>
- Configure the server (logs, content, etc.): <https://www.nginx.com/blog/deploying-nginx-nginx-plus-docker/#more-info>
- Configure logs output: <https://notestack.io/public/configure-nginx-logging-in-a-docker-container/874f1253-cf1a-4c62-9d2d-467ab23c258d>
