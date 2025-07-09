# SonarQube with PostgreSQL Docker Compose Setup

This project provides a Docker Compose configuration to run **SonarQube** with a **PostgreSQL** database backend. It is designed for easy local development and testing of SonarQube’s code quality and security analysis platform.

---

## Overview

- **SonarQube**: Continuous inspection tool for code quality and security.
- **PostgreSQL**: Database service used by SonarQube to store its data.
- **Docker Compose version**: 3.8

This setup uses persistent Docker volumes to maintain data across container restarts.

---

## Prerequisites

- Docker Engine installed (version compatible with Docker Compose 3.8)
- Docker Compose installed (version 1.27.0+ recommended)
- Minimum 2GB RAM available for SonarQube container to run smoothly

---

## Services

### sonarqube

- Image: `sonarqube:latest`
- Ports: Exposes port `9000` on the host for web UI access
- Depends on the `db` service to be ready before starting
- Environment variables configure JDBC connection to PostgreSQL
- Uses volumes for data and extensions persistence

### db

- Image: `postgres:15-alpine`
- Environment variables set up the database user, password, and database name
- Uses a volume to persist PostgreSQL data

---

## Usage

1. Clone or download this repository containing the `docker-compose.yml` file.

2. Start the services:

   > docker-compose up -d


3. Access SonarQube UI by navigating to:

http://localhost:9000


4. Default database credentials configured in this setup:

- Username: `sonar`  ( Test Username: admin if doesn't work with sonar )
- Password: `sonar`  ( Test Password: admin if doesn't work with sonar )
- Database: `sonarqube`

---

## Volumes

- `sonarqube_data`: Persists SonarQube application data
- `sonarqube_extensions`: Persists SonarQube plugins and extensions
- `postgresql_data`: Persists PostgreSQL database files

---

## Stopping and Removing Containers

To stop the services:

>  docker-compose down

## To remove volumes as well (data will be lost):

> docker-compose down -v

## Customization

- Modify environment variables under each service to change database credentials or SonarQube settings.
- Update image tags to use specific versions instead of `latest` for stability.
- Adjust ports if `9000` is already in use on your host machine.

---

## Troubleshooting

- Ensure Docker and Docker Compose versions support Compose file version 3.8.
- Check container logs for errors:

docker logs sonarqube
docker logs sonarqube_db

## References

- [SonarQube Docker Image](https://hub.docker.com/_/sonarqube)
- [PostgreSQL Docker Image](https://hub.docker.com/_/postgres)
- [Docker Compose File Reference (v3.8)](https://docs.docker.com/compose/compose-file/compose-versioning/#version-38)

---

*Created for easy deployment of SonarQube with PostgreSQL via Docker Compose.*
This README covers essential information about your Compose setup, usage instructions, customization tips, and troubleshooting advice, following professional standards.

