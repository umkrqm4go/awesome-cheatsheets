#!/usr/bin/env bash
# Docker Cheat Sheet

# --- BUILD ---
docker build -t image_name .
docker build -t image_name:tag .
docker build -f Dockerfile.dev -t image_name .
docker build --no-cache -t image_name .
docker build --build-arg HTTP_PROXY=http://10.20.30.40:1234 .

# --- BUILDX (Multi-platform) ---
docker buildx create --use --name mybuilder
docker buildx build --platform linux/amd64,linux/arm64 -t image_name:tag --push .

# --- RUN ---
docker run -d -p 8080:80 --name my_container image_name
docker run -it --rm image_name /bin/bash
docker run -v $(pwd):/app image_name
docker run --env-file .env image_name
docker run --restart=always image_name

# --- CONTAINERS ---
docker ps
docker ps -a
docker stop container_id
docker start container_id
docker restart container_id
docker rm container_id
docker rm -f $(docker ps -aq) # Remove all containers

# --- IMAGES ---
docker images
docker rmi image_name
docker rmi $(docker images -q) # Remove all images
docker image prune -a

# --- LOGS & EXEC ---
docker logs container_id
docker logs -f --tail 100 container_id
docker exec -it container_id /bin/bash
docker inspect container_id
docker stats

# --- NETWORKS ---
docker network ls
docker network create my_network
docker network connect my_network container_id
docker network inspect my_network

# --- VOLUMES ---
docker volume ls
docker volume create my_volume
docker volume inspect my_volume
docker volume prune

# --- CLEANUP ---
docker system prune -a --volumes