#!/usr/bin/env bash
# Docker cheatsheet

# --- IMAGES ---
# Build an image from a Dockerfile
docker build -t <image_name>:<tag> .

# Build without using cache
docker build --no-cache -t <image_name>:<tag> .

# List local images
docker images

# Remove an image
docker rmi <image_id>

# Remove dangling (unused) images
docker image prune

# Remove all unused images
docker image prune -a

# --- CONTAINERS ---
# Run a container in detached mode with port mapping
docker run -d -p <host_port>:<container_port> --name <container_name> <image_name>

# Run an interactive container and remove it after exit
docker run --rm -it <image_name> /bin/bash

# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# Stop a container
docker stop <container_id>

# Start a stopped container
docker start <container_id>

# Restart a container
docker restart <container_id>

# Remove a stopped container
docker rm <container_id>

# Force remove a running container
docker rm -f <container_id>

# --- LOGS & MONITORING ---
# View container logs
docker logs <container_id>

# Follow container logs in real time
docker logs -f --tail 100 <container_id>

# Display resource usage stats of running containers
docker stats

# Inspect container details
docker inspect <container_id>

# --- EXEC & SHELL ---
# Execute a command inside a running container
docker exec -it <container_id> /bin/sh

# --- CLEANUP ---
# Clean up stopped containers, unused networks, and dangling images
docker system prune -f

# Clean up everything including unused volumes
docker system prune -a --volumes -f