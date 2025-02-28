<p align="center">
    <picture>
        <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/traefik/traefik/master/docs/content/assets/img/traefik.logo-dark.png">
        <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/traefik/traefik/master/docs/content/assets/img/traefik.logo.png">
        <img alt="Traefik" title="Traefik" src="https://raw.githubusercontent.com/traefik/traefik/master/docs/content/assets/img/traefik.logo.png" width="250">
    </picture>
</p>

# Traefik

### Author: [Traefik Labs](https://github.com/traefik)
### Repository: [Traefik on GitHub](https://github.com/traefik/traefik)

A modern, cloud-native, and easy-to-use reverse proxy.

## About

Traefik is a **reverse proxy** and **load balancer** designed for modern cloud-native applications. It seamlessly integrates with **Docker**, **Kubernetes**, **Consul**, and various other orchestrators, automatically detecting services and routing traffic without extensive manual configuration.

## Features

- **Secure proxy with Docker Socket Proxy**: Reduces Traefik's system permissions.

- **Advanced IP filtering**: Restricts access to authorized users.

- **Security headers**: Protection against XSS attacks, clickjacking, and content injection.

- **Automatic service discovery**: Dynamically updates routes when services start, stop, or change.

- **Built-in Let's Encrypt SSL**: Automatically generates and renews HTTPS certificates.

- **Powerful middleware**: Authentication, rate limiting, and custom routing.

- **Observability**: Detailed metrics, logging, and tracing support.

- **Flexible deployment**: Compatible with Docker, Kubernetes, Swarm, Consul, and more.

- **Dashboard**: Intuitive web interface for monitoring and managing traffic routes.

## Containers

| Name         | Description                                    | Ports   |
|-------------|----------------------------------------------|-------- |
| traefik     | Reverse proxy managing containerized services | 80, 443 |
| socket-proxy | Secure proxy limiting access to Docker socket | 2375    |

## Advanced Security with Docker Socket Proxy and IP Filtering

Traefik uses Docker Socket Proxy to secure access to the Docker socket, preventing risks associated with direct daemon exposure.

Additionally, IP filtering can be enabled to restrict access to the dashboard and services. To enable it, add the authorized IP addresses in the `.env` file under the variable `ALLOWED_IPS`.

Example configuration in `.env`:

```ini
# List of IPs allowed to access the dashboard and secured services
ALLOWED_IPS=192.168.1.1,192.168.1.2

# List of IPs allowed to access other services protected by an IP Whitelist
SERVICE_ALLOWED_IPS=192.168.1.1,192.168.1.2
```

If you do not wish to enable this restriction, you can comment out or remove these lines in `docker-compose.yml`:

```yaml
- "traefik.http.routers.traefik-secure.middlewares=traefik-ipwhitelist"
- "traefik.http.middlewares.traefik-ipwhitelist.ipwhitelist.sourcerange=${ALLOWED_IPS}"
```

## Authentication Configuration

To secure the Traefik dashboard with basic authentication, follow these steps:

### Install `htpasswd`:

```bash
sudo apt update
sudo apt install apache2-utils
```

### Generate a user and password for the dashboard:

```bash
htpasswd -nbB user "MY_SECURE_PASSWORD"
```

This will generate a line formatted as:

```plaintext
user:$2y$05$abc123...
```

Replace `user` with your desired username and `MY_SECURE_PASSWORD` with your secure password.

### Modify the `.env` file and add:

```env
TRAEFIK_DASHBOARD_CREDENTIALS=user:hashpass
```

## Documentation

For detailed installation instructions and advanced configurations, check the [Official Traefik Documentation](https://doc.traefik.io/traefik).

## Community & Support

- [Community Forum](https://community.traefik.io/)
- [Twitter](https://twitter.com/intent/follow?screen_name=traefik)
- [GitHub Issues](https://github.com/traefik/traefik/issues)

