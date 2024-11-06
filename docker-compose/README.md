# Docker Compose Guide

- [Docker Compose Guide](#docker-compose-guide)
  - [Why Use Docker Compose?](#why-use-docker-compose)
  - [How to Use Docker Compose](#how-to-use-docker-compose)
    - [Example `docker-compose.yml` file](#example-docker-composeyml-file)
  - [Requirements to Use Docker Compose](#requirements-to-use-docker-compose)
    - [Installation Guide](#installation-guide)
  - [Where to Store the Docker Compose File](#where-to-store-the-docker-compose-file)
  - [Common Docker Compose Commands](#common-docker-compose-commands)
    - [Managing Your Application](#managing-your-application)
      - [Starting the Application (Without Detached Mode)](#starting-the-application-without-detached-mode)
      - [Starting the Application (In Detached Mode)](#starting-the-application-in-detached-mode)
      - [Difference Between Running with or without Detached Mode](#difference-between-running-with-or-without-detached-mode)
      - [Stopping the Application](#stopping-the-application)
      - [Running the Application in Detached Mode](#running-the-application-in-detached-mode)
      - [Checking Services Running with Docker Compose](#checking-services-running-with-docker-compose)
      - [Viewing Logs in Real-Time](#viewing-logs-in-real-time)
      - [Viewing Docker Compose Images](#viewing-docker-compose-images)
  - [Summary](#summary)

## Why Use Docker Compose?

Docker Compose is a tool used to define and run multi-container Docker applications. With Docker Compose, you can manage applications that require multiple services (such as databases, web servers, and application servers) easily. It helps streamline the development, testing, and deployment processes by:

- Enabling you to define and control all your application services in one configuration file (`docker-compose.yml`).
- Simplifying the commands needed to start, stop, and manage multi-container Docker applications.
- Facilitating a reproducible and consistent environment across different stages (development, staging, production).

## How to Use Docker Compose

Docker Compose allows you to define services in a `docker-compose.yml` file and run them with a single command.

Basic steps to use Docker Compose:

1. **Create a `docker-compose.yml` file** with the configuration for your services.
2. **Run commands** using Docker Compose CLI to start, stop, and manage these services.

### Example `docker-compose.yml` file

```yaml
version: '3'
services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: example
```

## Requirements to Use Docker Compose

To use Docker Compose, you need:

1. **Docker**: Docker should be installed and running on your system.
2. **Docker Compose**: Docker Desktop includes Docker Compose by default, but you can also install it separately if needed.

### Installation Guide

1. Install **Docker** by following instructions from [Docker's official documentation](https://docs.docker.com/get-docker/).
2. Verify that Docker Compose is available by running:

   ```bash
   docker-compose --version
   ```

## Where to Store the Docker Compose File

The `docker-compose.yml` file should be stored in the root directory of your project. This is where Docker Compose will look by default when you run commands in that directory.

## Common Docker Compose Commands

### Managing Your Application

Docker Compose commands allow you to manage your application's lifecycle easily. Here are some commonly used commands:

#### Starting the Application (Without Detached Mode)

To start the application in the foreground (without detached mode), run:

```bash
docker-compose up
```

This command will display logs for each service in your terminal.

#### Starting the Application (In Detached Mode)

To start the application in detached mode (in the background), use:

```bash
docker-compose up -d
```

#### Difference Between Running with or without Detached Mode

- **Without Detached Mode**: The `docker-compose up` command runs in the foreground and shows logs of all services in real-time. It requires the terminal to remain open.
- **With Detached Mode**: The `docker-compose up -d` command runs in the background, so you don’t see logs immediately and can use the terminal for other tasks.

#### Stopping the Application

To stop the running services, use:

```bash
docker-compose down
```

This command stops and removes the containers defined in your `docker-compose.yml` file.

#### Running the Application in Detached Mode

To run your application in detached mode (if not already running), simply use:

```bash
docker-compose up -d
```

#### Checking Services Running with Docker Compose

To check the status of services in your Docker Compose application, use:

```bash
docker-compose ps
```

#### Viewing Logs in Real-Time

To view logs in real-time for all services in your Docker Compose application, use:

```bash
docker-compose logs -f
```

#### Viewing Docker Compose Images

To view all images used by your Docker Compose file, use:

```bash
docker-compose images
```

## Summary

Docker Compose provides a powerful, efficient way to manage multi-container applications. By defining services in a single `docker-compose.yml` file, you can start, stop, and manage all your application services with ease. Whether you're working in detached mode or interacting with logs, Docker Compose offers the flexibility to suit your workflow.
