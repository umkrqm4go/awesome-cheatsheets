#!/bin/bash
# Docker cheatsheet

# --- IMAGES ---
# Build image from Dockerfile
docker build -t <image_name> .

# Build image without using cache
docker build --no-cache -t <image_name> .

# List local images
docker images

# Delete an image
docker rmi <image_id>

# Remove unused images
docker image prune -a

# --- CONTAINERS ---
# Run a container in detached mode with port mapping
docker run -d -p <host_port>:<container_port> --name <container_name> <image_name>

# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# Stop a running container
docker stop <container_id>

# Start a stopped container
docker start <container_id>

# Restart a container
docker restart <container_id>

# Remove a stopped container
docker rm <container_id>

# Remove all stopped containers
docker container prune

# --- LOGS & DEBUGGING ---
# View container logs
docker logs -f <container_name>

# Execute interactive shell inside running container
docker exec -it <container_name> /bin/sh

# Inspect container details
docker inspect <container_name>

# Check resource usage statistics
docker stats

# --- CLEANUP ---
# Remove all unused containers, networks, images, and volumes
docker system prune -a --volumes