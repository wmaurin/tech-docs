# Docker Command Reference

## Images

```bash
# List images
docker images
docker image ls

# Pull an image
docker pull <image>:<tag>

# Build an image
docker build -t <name>:<tag> .
docker build -t <name>:<tag> -f <Dockerfile> .

# Remove images
docker rmi <image>
docker image prune           # Remove dangling images
docker image prune -a        # Remove all unused images

# Tag an image
docker tag <source> <target>

# Push to registry
docker push <image>:<tag>
```

## Containers

```bash
# List containers
docker ps                    # Running containers
docker ps -a                 # All containers

# Run a container
docker run <image>
docker run -d <image>                    # Detached mode
docker run -it <image> /bin/bash         # Interactive with TTY
docker run --name <name> <image>         # Named container
docker run -p 8080:80 <image>            # Port mapping
docker run -v /host:/container <image>   # Volume mount
docker run --rm <image>                  # Remove after exit
docker run -e VAR=value <image>          # Environment variable
docker run --env-file .env <image>       # Env file

# Container lifecycle
docker start <container>
docker stop <container>
docker restart <container>
docker kill <container>

# Remove containers
docker rm <container>
docker rm -f <container>     # Force remove running
docker container prune       # Remove stopped containers
```

## Container Interaction

```bash
# Execute command in container
docker exec <container> <command>
docker exec -it <container> /bin/bash    # Interactive shell

# View logs
docker logs <container>
docker logs -f <container>               # Follow logs
docker logs --tail 100 <container>       # Last 100 lines

# Copy files
docker cp <container>:/path /local/path
docker cp /local/path <container>:/path

# Inspect container
docker inspect <container>

# View resource usage
docker stats
docker stats <container>
```

## Volumes

```bash
# List volumes
docker volume ls

# Create volume
docker volume create <name>

# Inspect volume
docker volume inspect <name>

# Remove volumes
docker volume rm <name>
docker volume prune          # Remove unused volumes
```

## Networks

```bash
# List networks
docker network ls

# Create network
docker network create <name>

# Connect/disconnect container
docker network connect <network> <container>
docker network disconnect <network> <container>

# Inspect network
docker network inspect <name>

# Remove network
docker network rm <name>
```

## Docker Compose

```bash
# Start services
docker compose up
docker compose up -d         # Detached mode
docker compose up --build    # Rebuild images

# Stop services
docker compose down
docker compose down -v       # Also remove volumes

# View logs
docker compose logs
docker compose logs -f <service>

# List services
docker compose ps

# Execute command in service
docker compose exec <service> <command>

# Scale services
docker compose up -d --scale <service>=3
```

## System Cleanup

```bash
# View disk usage
docker system df

# Clean up everything unused
docker system prune
docker system prune -a       # Include unused images
docker system prune --volumes # Include volumes
```

