# Docker Microservices Architecture Project

A complete journey from basic containerization to production-ready microservices with Docker and Docker Compose.

## Overview

This project demonstrates the evolution from a simple static website container to a horizontally scalable microservices architecture with load balancing and service isolation.

**Architecture Evolution:**
- Task 1-2: Basic static container + project organization
- Task 3: Dynamic front-end with API integration
- Task 4: Docker Compose orchestration
- Task 5: Reverse proxy with single entry point
- Task 6: Horizontal scaling with load balancing

## Quick Start

```bash
# Clone and navigate to final version
git clone <repository-url>
cd task6

# Run with 2 backend instances
docker-compose up --scale back-end=2

# Access application
open http://localhost
```

## Final Architecture (Task 6)

```
Browser → Proxy (Port 80) → Front-End (Internal)
                         → Back-End Instance 1
                         → Back-End Instance 2
```

**Key Features:**
- Single entry point through reverse proxy
- Automatic load balancing across backend instances
- Service isolation (internal services not directly accessible)
- Zero-configuration horizontal scaling

## Project Structure

```
task6/
├── docker-compose.yml          # Service orchestration
├── back-end/
│   ├── Dockerfile
│   └── api.py                  # Flask API
├── front-end/
│   ├── Dockerfile
│   └── softy-pinko-front-end/  # Static website
└── proxy/
    ├── Dockerfile
    └── proxy.conf              # Nginx routing
```

## Technology Stack

- **Web Server**: Nginx (static content + reverse proxy)
- **API Server**: Flask (Python)
- **Frontend**: HTML/CSS/JavaScript
- **Orchestration**: Docker Compose
- **Load Balancing**: Nginx upstream

## Key Commands

```bash
# Build all services
docker-compose build

# Start normally
docker-compose up

# Start with scaling
docker-compose up --scale back-end=3

# Stop all services
docker-compose down

# View logs
docker-compose logs

# Test API
curl http://localhost/api/hello
```

## Key Concepts Demonstrated

- **Containerization**: Docker fundamentals and multi-service applications
- **Service Orchestration**: Docker Compose for managing multiple containers
- **Reverse Proxy**: Single entry point routing with Nginx
- **Load Balancing**: Automatic request distribution across instances
- **Horizontal Scaling**: Adding capacity through container replication
- **Network Security**: Internal service isolation behind proxy

## Production Features

- **Single Domain**: All services accessible through one endpoint
- **Auto-scaling**: Easy addition of backend instances
- **Zero Downtime**: Scale without service interruption
- **Security**: Backend services isolated from direct access
- **Load Distribution**: Round-robin request balancing

## Troubleshooting

**Port conflicts:**
```bash
docker-compose down
docker stop $(docker ps -q)
```

**Check logs:**
```bash
docker-compose logs service-name
```

**Verify scaling:**
Refresh the page and watch terminal logs alternate between backend instances:
```
back-end_1 | GET /api/hello HTTP/1.0" 200
back-end_2 | GET /api/hello HTTP/1.0" 200
```

## Author
Josniel Ramos
