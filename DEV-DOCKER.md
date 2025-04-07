# Langfuse Development Docker Setup

This Docker Compose setup provides a complete development environment for Langfuse, with hot-reloading for local code changes.

## Features

- Single command to start the entire development stack
- Hot-reloading of local code changes
- Pre-configured infrastructure (PostgreSQL, ClickHouse, Redis, MinIO)
- Persistent volumes for database data and dependencies
- Properly cached node_modules for faster startup

## Requirements

- Docker and Docker Compose
- Git

## Usage

### Starting the development environment

```bash
# Clone the repository if you haven't already
git clone https://github.com/langfuse/langfuse.git
cd langfuse

# Start the development environment
docker compose -f docker-compose.dev.local.yml up
```

To run in detached mode (background):

```bash
docker compose -f docker-compose.dev.local.yml up -d
```

### Viewing logs

```bash
# View logs of all services
docker compose -f docker-compose.dev.local.yml logs -f

# View logs of a specific service
docker compose -f docker-compose.dev.local.yml logs -f dev
```

### Stopping the environment

```bash
docker compose -f docker-compose.dev.local.yml down
```

To remove volumes and completely reset:

```bash
docker compose -f docker-compose.dev.local.yml down -v
```

## Accessing Services

- **Langfuse Web UI**: http://localhost:3000
- **MinIO Console**: http://localhost:9091 (Login: minio / miniosecret)
- **PostgreSQL**: localhost:5432 (User: postgres / Password: postgres)
- **ClickHouse**: http://localhost:8123 (User: clickhouse / Password: clickhouse)

## Development Workflow

1. Make changes to the code on your local machine
2. Changes will automatically be detected and the application will hot-reload
3. View the results in your browser

## Customization

You can modify the environment variables in the `docker-compose.dev.local.yml` file to change configuration settings.

## Troubleshooting

If you encounter issues:

1. Check the logs: `docker compose -f docker-compose.dev.local.yml logs -f`
2. Restart the stack: `docker compose -f docker-compose.dev.local.yml restart`
3. Reset completely: `docker compose -f docker-compose.dev.local.yml down -v && docker compose -f docker-compose.dev.local.yml up`
