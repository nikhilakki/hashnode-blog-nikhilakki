---
title: "Handling environment variables in Containers (Docker/Podman)"
seoTitle: "Handling environment variables in Containers (Docker/Podman)"
datePublished: Sat Jan 14 2023 10:40:41 GMT+0000 (Coordinated Universal Time)
cuid: clcvti62d01s9usnv4dxw07rh
slug: handling-environment-variables-in-containers-dockerpodman
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1672952864230/608588db-df80-4e22-a97a-cd4329a3b0b4.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1672953147774/4adb8198-e90c-42f2-9393-9654f092db8c.jpeg
tags: microservices, docker, containers, podman, environment-variables

---

Environment variables are an essential way to configure your services. They make it easy to configure services for different environments & deployments.

There are several ways to handle environment variables in containers:

1. You can pass them directly to the container at runtime using the `-e` flag, like this:
    

```bash
$ docker run -e VAR_NAME=value -e VAR_NAME2=value2 image_name
```

2. You can also set environment variables in the `Dockerfile` for your image. This can be done using the `ENV` directive, like this:
    
```plaintext
ENV VAR_NAME value
ENV VAR_NAME2 value2
```

3. You can use a `.env` file to store your environment variables and pass them to the container at runtime using the `--env-file` flag:
    

```bash
$ docker run --env-file .env image_name
```

The `.env` file should contain one `VAR_NAME=value` pair per line.

```plaintext
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_PORT=5432
POSTGRES_DB=my-db
```

4. You can also pass environment variables to a container when using `docker-compose`. To do this, you can set them in the `environment` section of the `docker-compose.yml` file, like this:

```yaml
version: '3'
services:
web:
    environment:
    - VAR_NAME=value
    - VAR_NAME2=value2
    image: image_name
```

In Podman, you can use the same flags and methods to handle environment variables.

### Takeaway -

A full working example of this article can be found below.

%[https://github.com/nikhilakki/docker-env-poc]