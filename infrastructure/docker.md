# Docker Cheat Sheet

### Basic Docker Commands

- `docker run <image>`: Run a container from an image.
- `docker ps`: List running containers.
- `docker stop <container>`: Stop a running container.
- `docker rm <container>`: Remove a stopped container.
- `docker images`: List available images.
- `docker rmi <image>`: Remove an image.

### Building and Managing Images

- `docker build -t <image_name> <path_to_dockerfile>`: Build an image from a Dockerfile.
- `docker push <image>`: Push an image to a registry.
- `docker pull <image>`: Pull an image from a registry.
- `docker tag <source_image> <target_image>`: Create a new tag for an image.

### Networking

- `docker network create <network>`: Create a network.
- `docker network connect <network> <container>`: Connect a container to a network.
- `docker network disconnect <network> <container>`: Disconnect a container from a network.

### Docker Volumes

- `docker volume create <volume>`: Create a volume.
- `docker volume ls`: List available volumes.
- `docker volume inspect <volume>`: Inspect details of a volume.
- `docker volume rm <volume>`: Remove a volume.

### Docker Compose Commands

- `docker-compose up`: Start containers defined in a Compose file.
- `docker-compose down`: Stop and remove containers, networks, and volumes defined in a Compose file.
- `docker-compose ps`: List containers managed by Docker Compose.
- `docker-compose logs <service>`: View logs of a specific service.
- `docker-compose exec <service> <command>`: Run a command in a running service container.

## Docker Compose Cheat Sheet

### Docker Compose File Structure

```yaml
version: '3'
services:
  service1:
    build: .
    image: myimage:latest
    ports:
      - 8080:80
    volumes:
      - ./app:/app
    environment:
      - ENV_VAR=value
  service2:
    image: nginx:latest
    ports:
      - 80:80
```

### Defining Services

- `services`: Defines the services that make up your application.
- `build`: Specifies the path to the Dockerfile for building an image.
- `image`: Specifies the pre-built image to use.
- `ports`: Exposes ports between the host and the container.
- `volumes`: Mounts host directories or named volumes to the container.
- `environment`: Sets environment variables inside the container.

### Running Docker Compose

- `docker-compose up`: Create and start containers.
- `docker-compose up -d`: Create and start containers in detached mode.
- `docker-compose down`: Stop and remove containers, networks, and volumes.
- `docker-compose logs <service>`: View logs of a specific service.
- `docker-compose exec <service> <command>`: Run a command in a running service container.

### Scaling Services

- `docker-compose up --scale <service>=<number>`: Scale a service to a specific number of instances.