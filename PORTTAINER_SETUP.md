# Portainer Setup Guide

## Overview
This guide explains how to set up Portainer for managing your Energen spa website containers.

## Prerequisites
- Docker and Docker Compose installed
- AWS credentials configured
- ECR repository created

## Setup Instructions

### 1. Environment Configuration
Copy the example environment file and configure your settings:
```bash
cp env.example .env
# Edit .env with your actual values
```

### 2. Start Portainer with Energen Web App
```bash
# Start both Portainer and your web application
docker-compose -f docker-compose-portainer.yml up -d
```

### 3. Access Portainer
- Open your browser and navigate to: `https://localhost:9443`
- Create an admin account on first login
- Use HTTP (port 9000) if you don't have SSL configured

### 4. Access Your Web Application
- Your Energen spa website will be available at: `http://localhost`

## Portainer Features for Your Setup

### Container Management
- View real-time container logs
- Monitor resource usage
- Restart/stop containers
- Update container images

### Network Management
- View network topology
- Manage container networking
- Monitor network traffic

### Volume Management
- Manage persistent data
- Backup/restore volumes
- Monitor storage usage

### Security Features
- Container security scanning
- Access control and user management
- Audit logs
- Security policies

## Security Best Practices

### 1. Change Default Passwords
- Use strong passwords for Portainer admin account
- Rotate passwords regularly

### 2. Enable HTTPS
- Configure SSL certificates for Portainer
- Use secure connections only

### 3. Access Control
- Create specific users with limited permissions
- Use role-based access control (RBAC)
- Regular access reviews

### 4. Network Security
- Use firewalls to restrict access
- Consider VPN for remote access
- Monitor network traffic

## Troubleshooting

### Common Issues

1. **Portainer won't start**
   - Check if port 9000/9443 is available
   - Verify Docker daemon is running
   - Check container logs: `docker logs portainer`

2. **Cannot access web application**
   - Verify container is running: `docker ps`
   - Check health status: `docker inspect energen-web`
   - Review container logs: `docker logs energen-web`

3. **Permission issues**
   - Ensure Docker socket permissions are correct
   - Check user permissions for Portainer

### Useful Commands
```bash
# View running containers
docker ps

# Check container logs
docker logs portainer
docker logs energen-web

# Restart services
docker-compose -f docker-compose-portainer.yml restart

# Stop all services
docker-compose -f docker-compose-portainer.yml down

# Update Portainer
docker pull portainer/portainer-ce:latest
docker-compose -f docker-compose-portainer.yml up -d portainer
```

## Monitoring and Maintenance

### Regular Tasks
- Monitor container health
- Update Portainer regularly
- Review security logs
- Backup Portainer data
- Update base images

### Health Checks
The setup includes health checks for:
- Web application availability
- Container resource usage
- Network connectivity

## Support
For issues with:
- Portainer: Check [Portainer documentation](https://docs.portainer.io/)
- Docker: Check [Docker documentation](https://docs.docker.com/)
- This setup: Review this guide and container logs
