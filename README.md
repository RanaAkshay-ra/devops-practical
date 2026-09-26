# Docker Troubleshooting Lab

## Objective

Build and troubleshoot a containerised Nginx web service.

## Environment

- Windows
- Docker Desktop
- Linux/Alpine
- Nginx
- Git
- Nmap

## Problem

The application container was running but the website was not accessible
through localhost:8081.

## Investigation

Checked:

- Docker Engine status
- Running containers
- Docker Compose status
- Container logs
- Nginx service inside the Linux container
- Docker port mappings
- Docker networking

## Root Cause

The Docker Compose configuration mapped host port 8081 to container port 81.

Nginx was listening on port 80.

Incorrect:

8081:81

Correct:

8081:80

## Resolution

Changed the Docker Compose port mapping and recreated the container.

## Validation

Validated using:

docker ps

curl http://localhost:8081

docker logs devops-web

nmap -sV -p 8081 localhost

## Result

The Nginx service became accessible successfully through localhost:8081.
