
# Create a Docker image

- [Create a Docker image](#create-a-docker-image)
  - [Prerequisites](#prerequisites)
  - [Docker Image from a Running Container](#docker-image-from-a-running-container)
    - [Full Example (abstract)](#full-example-abstract)
    - [Steps](#steps)
      - [1. Create a Container (if not already running)](#1-create-a-container-if-not-already-running)
      - [2. Commit the Running Container as an Image](#2-commit-the-running-container-as-an-image)
  - [Docker Image from a Dockerfile](#docker-image-from-a-dockerfile)
    - [Full Example (abstract)](#full-example-abstract-1)
    - [Steps](#steps-1)
      - [1. Create a Dockerfile](#1-create-a-dockerfile)
      - [2. Build the Image from Dockerfile](#2-build-the-image-from-dockerfile)
  - [Tag the image](#tag-the-image)
  - [Push the Image to Docker Hub](#push-the-image-to-docker-hub)
  - [Verify the Image on Docker Hub](#verify-the-image-on-docker-hub)
    - [Additional Tips](#additional-tips)

## Prerequisites

- Docker must be installed on your local machine.
- You need a Docker Hub account. You can sign up at [Docker Hub](https://hub.docker.com/).

## Docker Image from a Running Container

This guide covers how to:

1. **Create** a Docker image from a running container.
2. **Tag** the image appropriately.
3. **Push** the image to Docker Hub.

### Full Example (abstract)

Here’s a full example of creating and pushing an image from a running container:

```bash
# Step 1: Start a container
docker run -d -p 80:80 nginx

# Step 2: Commit the container to create an image
docker commit <container-id> <image_name>

# Step 3: Tag your image
docker tag <image_name> <dockerhub_username>/<image_name>:<tag>

# Step 4: Push the image to Docker Hub
docker push <dockerhub_username>/<image_name>:<tag>
```

### Steps

#### 1. Create a Container (if not already running)

If you don’t have a running container yet, you can start one. For example, to start an Nginx container:

```bash
docker run -d -p 80:80 nginx
```

This command runs the Nginx server in the background.

#### 2. Commit the Running Container as an Image

To create a Docker image from the running container, use the `docker commit` command:

```bash
docker commit <container_id> <image_name>:<tag>
```

- `<container_id>`: Replace this with the ID or name of your running container.
- `<image_name>`: The name you want for the new image.
- `<tag>`: A tag for versioning (e.g., `latest`).

For example:

```bash
docker commit <container_id> nginx-264
```

This command creates an image named `nginx-264` with the `latest` tag in your local Docker images.


## Docker Image from a Dockerfile

This guide covers how to:

1. **Create** a Docker image from a running container.
2. **Tag** the image appropriately.
3. **Push** the image to Docker Hub.

### Full Example (abstract)

Here’s a full example of creating and pushing an image from a running container:

```bash
docker build -t <folder_path>
```

### Steps

#### 1. Create a Dockerfile

For example, to create an Nginx webserver:

```dockerfile
# Use the official Nginx image from Docker Hub as the base image
FROM nginx:latest

# Copy any custom configuration files or HTML content, if needed
COPY ./index.html /usr/share/nginx/html/index.html
COPY ./video.mp4 /usr/share/nginx/html/video.mp4

# Expose port 80 to allow traffic to the container
EXPOSE 80
```

#### 2. Build the Image from Dockerfile

To create a Docker image from the dockerfile, use the `docker build` command:

```bash
docker build -t <folder_path>
```

- `<container_id>`: Replace this with the ID or name of your running container.
- `<image_name>`: The name you want for the new image.
- `<tag>`: A tag for versioning (e.g., `latest`).

---

## Tag the image

Before pushing the image to Docker Hub, ensure you’re logged in:

```bash
docker tag nginx-264 shonifari8/nginx-264:v1
```

Enter your Docker Hub credentials when prompted.

## Push the Image to Docker Hub

Now, push the newly created image to Docker Hub:

```bash
docker push <dockerhub_username>/<image_name>:<tag>
```

Using our example:

```bash
docker push shonifari8/nginx-264:v1
```

This command uploads the image to Docker Hub under your account.

## Verify the Image on Docker Hub

Go to [Docker Hub](https://hub.docker.com/) and navigate to your repository to verify that the image was successfully pushed.

### Additional Tips

- Use descriptive tags for versioning (e.g., `v1.0`, `stable`).
- You can also use `docker tag` to rename or retag images before pushing them:

  ```bash
  docker tag <existing_image> <your_dockerhub_username>/<new_image_name>:<new_tag>
  ```
