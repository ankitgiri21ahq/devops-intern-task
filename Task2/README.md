# DevOps Intern Task - Git Commands

This repository is part of my DevOps internship, demonstrating basic Docker commands.

# Useful Docker Commands and Dockerfile Guide

Docker is a platform for containerizing applications, enabling consistent development, testing, and deployment. This document lists the most useful Docker commands with their use cases and provides a detailed guide on Dockerfiles, including their purpose and common instructions.

## Useful Docker Commands

### Basic Commands
- **docker --version**: Displays the installed Docker version.
  - Use case: Verify that Docker is installed and check its version.

- **docker info**: Shows system-wide information about Docker, such as the number of containers and images.
  - Use case: Check Docker’s status and configuration on your system.

- **docker pull <image-name>**: Downloads a Docker image from a registry (e.g., Docker Hub).
  - Use case: Fetch an image (like `nginx` or `ubuntu`) to use locally.

### Container Management
- **docker run <image-name>**: Runs a container from a specified image.
  - Use case: Start a new container, e.g., `docker run nginx` to run an Nginx web server.

- **docker run -d <image-name>**: Runs a container in detached mode (in the background).
  - Use case: Run a container (like a database) without tying up the terminal.

- **docker ps**: Lists all running containers.
  - Use case: Check which containers are currently active.

- **docker ps -a**: Lists all containers, including stopped ones.
  - Use case: View all containers to manage or debug them.

- **docker stop <container-id>**: Stops a running container.
  - Use case: Gracefully stop a container, e.g., to shut down a test environment.

- **docker rm <container-id>**: Removes a stopped container.
  - Use case: Clean up unused containers to free up system resources.

### Image Management
- **docker images**: Lists all Docker images available locally.
  - Use case: Check which images are stored on your machine.

- **docker build -t <image-name> .**: Builds a Docker image from a Dockerfile in the current directory.
  - Use case: Create a custom image for your application.

- **docker rmi <image-id>**: Removes a Docker image.
  - Use case: Delete unused images to save disk space.

### Docker Compose
- **docker-compose up**: Starts services defined in a `docker-compose.yml` file.
  - Use case: Launch a multi-container application (e.g., web app + database) with one command.

- **docker-compose down**: Stops and removes containers defined in `docker-compose.yml`.
  - Use case: Shut down a multi-container setup cleanly.

### Networking and Volumes
- **docker network ls**: Lists all Docker networks.
  - Use case: Check available networks for container communication.

- **docker network create <network-name>**: Creates a custom Docker network.
  - Use case: Set up a network for containers to communicate securely.

- **docker volume create <volume-name>**: Creates a Docker volume for persistent data.
  - Use case: Store data (e.g., database files) outside of a container’s lifecycle.

- **docker run -v <volume-name>:/path <image-name>**: Mounts a volume to a container.
  - Use case: Persist data, like mounting a volume for a database container.

### Debugging and Inspection
- **docker logs <container-id>**: Shows the logs of a container.
  - Use case: Debug a container by checking its output or errors.

- **docker exec -it <container-id> /bin/bash**: Opens an interactive shell inside a running container.
  - Use case: Access a container to run commands or troubleshoot.

- **docker inspect <container-id>**: Displays detailed information about a container.
  - Use case: View configuration details, like network settings or environment variables.

### Cleanup
- **docker system prune**: Removes unused containers, networks, and images.
  - Use case: Free up disk space by cleaning up unused Docker resources.

- **docker container prune**: Removes all stopped containers.
  - Use case: Clean up stopped containers to declutter your system.

## Dockerfile Guide

### What is a Dockerfile?
A **Dockerfile** is a text file containing a set of instructions to build a Docker image. It defines the environment, dependencies, and configuration needed to run an application in a container. Docker uses these instructions to create a reproducible and portable image.

### Why Use a Dockerfile?
- **Consistency**: Ensures the same environment across development, testing, and production.
- **Automation**: Automates the process of setting up an application’s dependencies.
- **Portability**: Allows images to be shared and run on any system with Docker installed.
- **Version Control**: Dockerfiles can be versioned in Git, making it easy to track changes.

### Common Dockerfile Instructions
Below are the most commonly used Dockerfile instructions with their purposes and example usage:

- **FROM**: Specifies the base image to start with.
  - Use case: Set the foundation for your image, e.g., using an official image like `python` or `node`.
  - Example:
    ```dockerfile
    FROM ubuntu:20.04