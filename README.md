# Sikawan Filament Laravel Docker Deployment

This repository contains Docker configuration for deploying the Sikawan Filament Laravel application using MCP Docker.

## Environment

- PHP 8.2 (as specified in composer.json)
- SQLite database
- Nginx web server
- Laravel 12

## Deployment with MCP Docker

1. Clone your application repository:
```bash
git clone https://github.com/yourusername/sikawan-filament.git
cd sikawan-filament
```

2. Clone this Docker configuration repository:
```bash
git clone https://github.com/developerabdan/sikawan-filament-docker.git docker-config
cp -r docker-config/* docker-config/.dockerignore .
rm -rf docker-config
```

3. Deploy using Model Context Protocol:
```bash
# Initialize MCP Docker
mcp docker init

# Configure MCP deployment
mcp docker configure --compose-file docker-compose.mcp.yml

# Deploy the application
mcp docker deploy
```

4. Once deployed, set up the application:
```bash
# Run inside the container
mcp docker exec app composer install
mcp docker exec app php artisan migrate
mcp docker exec app php artisan key:generate
mcp docker exec app php artisan storage:link
```

## Environment Variables

The following environment variables should be set in your MCP Docker deployment:

- `APP_URL`: Your application URL
- `APP_KEY`: Laravel application key (will be generated)

## Accessing Your Application

After successful deployment, your application will be accessible at the URL provided by MCP Docker.