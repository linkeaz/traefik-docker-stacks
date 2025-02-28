<p align="center">
    <img src="https://raw.githubusercontent.com/louislam/dockge/master/frontend/public/icon.svg" width="100" alt="Dockge Logo" />
</p>

# Dockge

### Author: [Louis Lam](https://github.com/louislam)

### Repository: [Dockge on GitHub](https://github.com/louislam/dockge/tree/master)

An elegant, intuitive, and responsive manager for Docker Compose stacks.

## About

Dockge is a lightweight and efficient tool designed to manage **Docker Compose** stacks via a simple and intuitive user interface. It allows easy administration of multiple containerized services while providing an optimized and smooth management experience.

## Features

- **Simplified management** of Docker Compose stacks.
- **Intuitive user interface** for container administration.
- **Lightweight and responsive** for efficient use.
- **Full compatibility** with Docker Compose.
- **Secure access control** via IP whitelisting and security headers.

## Containers

| Name   | Description                              | Port |
| ------ | ---------------------------------------- | ---- |
| dockge | Web interface for managing Docker stacks | 5001 |

## Security Configuration

### IP Filtering (Optional)

Traefik allows enabling IP filtering to restrict access to Dockge. To enable it, add the authorized IP addresses in the `.env` file under the variable `SERVICE_ALLOWED_IPS`.

Example configuration in `.env`:

```ini
SERVICE_ALLOWED_IPS=192.168.1.1,192.168.1.2
```

If you do not want to enable this restriction, you can comment out or remove these lines in `docker-compose.yml`:

```yaml
- "traefik.http.routers.dockge.middlewares=dockge-ipwhitelist,security-headers"
- "traefik.http.middlewares.dockge-ipwhitelist.ipwhitelist.sourcerange=${SERVICE_ALLOWED_IPS}"
```

### Security Headers

Dockge benefits from additional security headers managed via Traefik. These headers protect against common security threats such as XSS, Clickjacking, and Content Sniffing.

## Documentation

For more information on installation and usage, check out the [Official Dockge Documentation](https://github.com/louislam/dockge/tree/master).

## Community & Support

- [GitHub Repository](https://github.com/louislam/dockge)
- [GitHub Issues](https://github.com/louislam/dockge/issues)

