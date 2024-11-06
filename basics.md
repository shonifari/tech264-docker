# Docker Common Commands

- [Docker Common Commands](#docker-common-commands)
  - [Installation and Setup](#installation-and-setup)
  - [Windows extra step](#windows-extra-step)
  - [Working with Images](#working-with-images)
  - [Working with Containers](#working-with-containers)
  - [Container Interaction](#container-interaction)
  - [Clean Up](#clean-up)
  - [Docker Compose](#docker-compose)
  - [Conclusion](#conclusion)

Docker is a powerful tool for creating, deploying, and managing containers. Below are some of the most commonly used Docker commands to help you get started.

## Installation and Setup

Before using Docker, ensure it is installed on your system. You can check the installation with:

```sh
docker --version
```

## Windows extra step

- **Create alias**: Needed to execute shell commands on containers

  ```sh
  alias docker="winpty docker"
  ```

## Working with Images

- **List Images**: Display all images on your system.

  ```sh
  docker images
  ```

- **Pull an Image**: Download an image from Docker Hub.

  ```sh
  docker pull <image_name>
  ```

- **Build an Image**: Create an image from a Dockerfile.

  ```sh
  docker build -t <image_name> .
  ```

- **Remove an Image**: Delete an image from your system.

  ```sh
  docker rmi <image_name>
  ```

## Working with Containers

- **Create and Run a Container**: Create and start a container from an image.

  ```sh
  docker run -d --name <container_name> <image_name>
  ```

- **List Running Containers**: Show all currently running containers.

  ```sh
  docker ps
  ```

- **List All Containers**: Show all containers, including stopped ones.

  ```sh
  docker ps -a
  ```

- **Stop a Container**: Stop a running container.

  ```sh
  docker stop <container_name>
  ```

- **Start a Container**: Start a stopped container.

  ```sh
  docker start <container_name>
  ```

- **Remove a Container**: Delete a stopped container.

  ```sh
  docker rm <container_name>
  ```

## Container Interaction

- **Access a Running Container**: Open a shell inside a running container.

  ```sh
  docker exec -it <container_name> sh
  ```

- **Fetch Container Logs**: View the logs of a container.

  ```sh
  docker logs <container_name>
  ```

- **Inspect a Container**: Get detailed information about a container.

  ```sh
  docker inspect <container_name>
  ```

## Clean Up

- **Remove Unused Images**: Clean up unused images to free up space.

  ```sh
  docker image prune
  ```

- **Remove Unused Containers**: Clean up stopped containers.

  ```sh
  docker container prune
  ```

## Docker Compose

Docker Compose is a tool for defining and running multi-container Docker applications.

- **Start Services**: Start all services defined in a `docker-compose.yml` file.

  ```sh
  docker-compose up
  ```

- **Stop Services**: Stop all running services.

  ```sh
  docker-compose down
  ```

## Conclusion

These commands cover the basics of working with Docker. For more detailed information, refer to the [Docker documentation](https://docs.docker.com/).
