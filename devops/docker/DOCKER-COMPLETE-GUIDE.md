# DOCKER COMPLETE GUIDE

## All Essential Commands & Concepts

## INSTALLATION

# Ubuntu/Debian

sudo apt update
sudo apt install docker.io docker-compose
sudo systemctl start docker
sudo systemctl enable docker

# Check

docker --version
docker-compose --version
sudo docker run hello-world

## SYSTEM COMMANDS

docker version # Version info
docker info # System info
docker system df # Disk usage
docker system prune # Remove unused data
docker system prune -a # Remove ALL unused data
docker stats # Live container stats
docker events # Real-time events

## IMAGE MANAGEMENT

### Pull/Search Images

docker pull ubuntu:latest
docker pull nginx:alpine
docker pull python:3.9-slim
docker search nginx

### List/Inspect Images

docker images # All images
docker images -a # All (including intermediate)
docker images --filter "dangling=true"
docker image ls # Alias for docker images
docker history <image> # Image layers
docker inspect <image> # Detailed info
docker tag <old> <new> # Tag image
docker save <image> > file.tar # Export image
docker load < file.tar # Import image

### Remove Images

docker rmi <image_id> # Remove image
docker rmi $(docker images -q) # Remove all images
docker image prune # Remove unused
docker image prune -a # Remove all unused

## CONTAINER MANAGEMENT

### Create & Run Containers

docker run [OPTIONS] IMAGE [CMD]

# Common Options:

# -d, --detach Run in background

# -it Interactive with TTY

# --name NAME Assign name

# -p HOST:CONTAINER Port mapping

# -v HOST:CONTAINER Volume mount

# -e KEY=VALUE Environment variable

# --network NETWORK Connect to network

# --restart POLICY Restart policy

### Examples:

docker run -d --name web nginx
docker run -it --rm ubuntu bash
docker run -p 8080:80 nginx
docker run -v /host:/container nginx
docker run -e MY_ENV=value app
docker run --network mynet app

### Container Lifecycle

docker start <container> # Start
docker stop <container> # Stop gracefully
docker stop -t 30 <container> # Stop with timeout
docker kill <container> # Force stop
docker restart <container> # Restart
docker pause <container> # Pause
docker unpause <container> # Unpause
docker wait <container> # Wait for exit

### List Containers

docker ps # Running containers
docker ps -a # All containers
docker ps -l # Last created
docker ps -q # Only IDs
docker ps --filter "status=running"
docker ps --filter "name=web"
docker ps --format "table {{.ID}}\t{{.Names}}\t{{.Status}}"

### Container Operations

docker exec -it <container> bash # Open shell
docker exec <container> ls -la # Run command
docker logs <container> # Show logs
docker logs -f <container> # Follow logs
docker logs --tail 50 <container> # Last 50 lines
docker top <container> # Running processes
docker port <container> # Port mappings
docker inspect <container> # Detailed info
docker diff <container> # Changed files
docker commit <container> <image> # Create image from container
docker export <container> > file.tar # Export container
docker import file.tar # Import as image
docker cp file.txt <container>:/path/ # Copy to container
docker cp <container>:/file.txt ./ # Copy from container

### Remove Containers

docker rm <container> # Remove stopped
docker rm -f <container> # Force remove running
docker rm $(docker ps -aq) # Remove all stopped
docker container prune # Remove all stopped
docker rm -v <container> # Remove with volumes

## 🏗️ BUILD IMAGES (Dockerfile)

### Dockerfile Template:

dockerfile

# Multi-stage example

FROM node:14-alpine AS builder
WORKDIR /app
COPY package\*.json ./
RUN npm ci --only=production
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

Build Commands:
docker build -t myapp:latest . # Build from current dir
docker build -t myapp:v1.0 -f Dockerfile.dev . # Custom Dockerfile
docker build --no-cache -t myapp . # Build without cache
docker build --build-arg KEY=value . # With build args

🌐 NETWORKING
Network Commands
docker network ls # List networks
docker network create mynet # Create network
docker network inspect mynet # Network details
docker network rm mynet # Remove network
docker network prune # Remove unused networks
docker network connect mynet container # Connect container
docker network disconnect mynet container # Disconnect

Network Types:
bridge (default) - NAT isolation
host - Use host network
none - No networking
overlay - Multi-host (Swarm)
Examples:
docker run --network bridge nginx # Default
docker run --network host nginx # Host network
docker run --network none nginx # No network
docker run --network mynet --name web nginx # Custom network

💾 VOLUMES & STORAGE
Volume Commands
docker volume ls # List volumes
docker volume create myvol # Create volume
docker volume inspect myvol # Volume details
docker volume rm myvol # Remove volume
docker volume prune # Remove unused volumes

Mount Types:

1. Bind Mounts (-v /host:/container)
   docker run -v /host/path:/container/path nginx

2. Named Volumes (-v name:/container)
   docker run -v myvol:/data nginx

3. tmpfs Mounts (--tmpfs /app)
   docker run --tmpfs /tmp nginx

Examples:
docker run -v /home/user/data:/app/data nginx # Bind mount
docker run -v mydata:/var/lib/mysql mysql # Named volume
docker run --mount type=bind,source=/home,target=/app nginx
docker run --mount type=volume,source=mydata,target=/data nginx

🚀 DOCKER COMPOSE
docker-compose.yml Example:
yaml
version: '3.8'
services:
web:
image: nginx:alpine
ports: - "80:80"
volumes: - ./html:/usr/share/nginx/html
depends_on: - db
environment: - DB_HOST=db

db:
image: postgres:13
environment:
POSTGRES_PASSWORD: secret
volumes: - postgres_data:/var/lib/postgresql/data

volumes:
postgres_data:
Compose Commands:
docker-compose up # Start services
docker-compose up -d # Start in background
docker-compose down # Stop and remove
docker-compose down -v # Remove with volumes
docker-compose ps # List services
docker-compose logs # Show logs
docker-compose logs -f # Follow logs
docker-compose logs web # Logs for specific service
docker-compose exec web bash # Execute in service
docker-compose exec db psql -U postgres
docker-compose build # Build images
docker-compose build --no-cache # Build without cache
docker-compose restart # Restart services
docker-compose restart web # Restart specific
docker-compose stop # Stop services
docker-compose start # Start services
docker-compose pause # Pause services
docker-compose unpause # Unpause services
docker-compose top # Show processes
docker-compose config # Validate config
docker-compose pull # Pull images
docker-compose push # Push images
docker-compose rm # Remove stopped containers
docker-compose run web bash # Run one-off command
docker-compose scale web=3 # Scale service (deprecated in v3)
docker-compose up --scale web=3 # Scale in v3

🛡️ DOCKERFILE BEST PRACTICES
Security:
dockerfile

# Use non-root user

FROM alpine
RUN addgroup -g 1000 appuser && \
 adduser -u 1000 -G appuser -s /bin/sh -D appuser
USER appuser

# Health check

HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
 CMD curl -f http://localhost/ || exit 1
Optimization:
dockerfile

# Combine RUN commands

RUN apt-get update && \
 apt-get install -y package1 package2 && \
 rm -rf /var/lib/apt/lists/\*

# Copy in stages

COPY package.json package-lock.json ./
RUN npm install
COPY . .

# Use .dockerignore

# node_modules/

# .git/

# \*.log

🔍 INSPECTION & DEBUGGING
docker inspect <object> # Inspect any Docker object
docker inspect --format='{{.NetworkSettings.IPAddress}}' container
docker inspect --format='{{json .Config}}' container
docker inspect --format='{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container

Check container health
docker ps --filter "health=healthy"
docker ps --filter "health=unhealthy"

Resource limits
docker run --memory="512m" --cpus="1.5" nginx
docker run --memory-swap="1g" nginx

🔄 REGISTRY OPERATIONS
Login/Logout
docker login
docker login registry.example.com
docker logout

Tag & Push
docker tag myapp:latest username/myapp:latest
docker tag myapp:latest username/myapp:v1.0
docker push username/myapp:latest
docker pull username/myapp:latest

Private registry
docker pull registry.example.com/myapp:latest
docker push registry.example.com/myapp:latest

🎯 QUICK COMMANDS REFERENCE
Cleanup everything
docker system prune -a --volumes

Stop all containers
docker stop $(docker ps -aq)

Remove all containers
docker rm $(docker ps -aq)

Remove all images
docker rmi $(docker images -q)

View container IP
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container

Backup container
docker export container > backup.tar
cat backup.tar | docker import - backup:latest

Copy database dump
docker exec -t db pg_dumpall -c -U postgres > dump.sql
cat dump.sql | docker exec -i db psql -U postgres

🏁 RESTART POLICIES
docker run --restart=always nginx # Always restart
docker run --restart=on-failure nginx # On failure only
docker run --restart=unless-stopped nginx # Unless manually stopped
docker run --restart=no nginx # No restart (default)

📝 ENVIRONMENT FILES
Using env file
docker run --env-file .env nginx

.env file format:
DB_HOST=localhost
DB_PORT=5432
🎮 USEFUL ALIASES (add to ~/.bashrc)
alias dps='docker ps --format "table {{.ID}}\t{{.Names}}\t{{.Status}}\t{{.Ports}}"'
alias dls='docker ps -a --format "table {{.ID}}\t{{.Names}}\t{{.Status}}\t{{.Ports}}"'
alias dim='docker images'
alias drm='docker rm'
alias drmi='docker rmi'
alias dstop='docker stop'
alias dstart='docker start'
alias dlog='docker logs -f'
alias dexec='docker exec -it'
alias dcu='docker-compose up'
alias dcd='docker-compose down'
alias dcl='docker-compose logs -f'
alias dce='docker-compose exec'
alias dcp='docker-compose ps'

⚠️ TROUBLESHOOTING
Check Docker daemon
sudo systemctl status docker
sudo journalctl -u docker.service

Reset Docker (WARNING: removes all data)
sudo systemctl stop docker
sudo rm -rf /var/lib/docker
sudo systemctl start docker

Permission denied error
sudo usermod -aG docker $USER
newgrp docker # Or logout/login

Out of disk space
docker system prune -a
docker volume prune

Debug container startup
docker run --rm -it --entrypoint sh image_name

Find large images/containers
docker system df -v

🎓 PRACTICE SCENARIOS

1. Web app with database
   docker network create app-network
   docker run -d --name db --network app-network -e POSTGRES_PASSWORD=pass postgres
   docker run -d --name app --network app-network -p 3000:3000 -e DB_HOST=db myapp

2. Development with volumes
   docker run -d --name dev -p 8080:80 -v $(pwd):/app -w /app node npm run dev

3. Production-like setup
   docker-compose -f docker-compose.prod.yml up -d

4. Multi-container monitoring
   docker stats $(docker ps --format={{.Names}})

📊 MONITORING
Live stats for all containers
docker stats --all --format "table {{.Name}}\t{{.CPUPerc}}\t{{.MemUsage}}\t{{.NetIO}}\t{{.BlockIO}}"

Resource usage per container
docker stats --no-stream container1 container2

🚨 EMERGENCY COMMANDS
Force remove everything
docker rm -f $(docker ps -aq)
docker rmi -f $(docker images -q)
docker volume rm $(docker volume ls -q)
docker network rm $(docker network ls -q)

Quick stop and cleanup
docker stop $(docker ps -q) && docker system prune -a -f

Save all running containers
docker ps -q | xargs docker commit -m "backup"

💡 PRO TIPS
Use docker-compose for development

Implement health checks

Use multi-stage builds

Mount configs as read-only volumes

Set resource limits (CPU, memory)

Use specific image tags (not latest)

Keep containers stateless

Use .dockerignore file

Scan images for vulnerabilities

Regular system cleanup

📚 ESSENTIAL FILES
.dockerignore example:
text
node_modules
.git
_.log
.env
Dockerfile_
docker-compose*
README.md
.gitignore
.vscode
.idea
*.swp
\*.swo
docker-compose.override.yml (development):
yaml
version: '3.8'
services:
web:
volumes: - ./src:/app/src
command: npm run dev
environment:
NODE_ENV: development

## MASTER COMMANDS CHEATSHEET

Container Lifecycle: run → start → stop → restart → rm
Image Management: pull → build → tag → push → rmi
Networking: network create → connect → inspect
Volumes: volume create → mount → prune
Compose: up → down → logs → exec → ps
System: info → stats → prune → events
REMEMBER: Containers are ephemeral, images are immutable!
