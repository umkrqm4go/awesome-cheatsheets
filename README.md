#!/usr/bin/env bash
# Docker Cheat Sheet

# --- BUILD ---
docker build -t image_name .                            # Build an image from a Dockerfile
docker build -t image_name:tag .                        # Build an image with a specific tag
docker build -f /path/to/Dockerfile .                   # Build using a specific Dockerfile
docker build --no-cache -t image_name .                 # Build without using cache
docker buildx build --platform linux/amd64,linux/arm64 -t image_name:latest . # Multi-architecture build

# --- RUN ---
docker run -d -p 8080:80 --name my_app image_name       # Run container in background mapping ports
docker run -it --rm image_name bash                     # Run interactive container and remove on exit
docker run -v /host/path:/container/path image_name     # Mount a host directory inside container
docker run --env-file .env image_name                   # Run container with environment variables from file

# --- MANAGE ---
docker ps                                               # List running containers
docker ps -a                                            # List all containers (running and stopped)
docker stop container_id                                # Stop a running container
docker start container_id                               # Start a stopped container
docker restart container_id                             # Restart a container
docker rm container_id                                  # Remove a container
docker rm -f container_id                               # Force remove a running container

# --- IMAGES ---
docker images                                           # List local images
docker rmi image_id                                     # Remove an image
docker rmi $(docker images -f "dangling=true" -q)       # Remove unused/dangling images
docker pull image_name                                  # Pull image from registry
docker push image_name                                  # Push image to registry

# --- LOGS & INSPECT ---
docker logs -f container_id                             # Stream container logs
docker logs --tail 100 container_id                     # Show last 100 lines of logs
docker exec -it container_id bash                       # Execute bash command inside running container
docker inspect container_id                             # Display detailed container information
docker stats                                            # Display live stream of container resource usage

# --- CLEANUP ---
docker system prune -a --volumes                        # Remove all unused containers, networks, images, and volumes
docker volume prune                                     # Remove all unused local volumes
docker network prune                                    # Remove all unused networks