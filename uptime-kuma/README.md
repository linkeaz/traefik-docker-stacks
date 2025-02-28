<p align="center">
    <img src="https://raw.githubusercontent.com/louislam/uptime-kuma/master/public/icon.svg" width="150" alt="Uptime Kuma Logo" />
</p>

# Uptime Kuma

### Author: [Louis Lam](https://github.com/louislam)
### Repository: [Uptime Kuma on GitHub](https://github.com/louislam/uptime-kuma)

An open-source alternative to "Uptime Robot" for monitoring service availability.

## About

Uptime Kuma is a simple, self-hosted uptime monitor that allows you to track the status of your servers and services. It features a modern web interface and offers advanced notifications.

This project includes an **optimized configuration** for **secure usage**, especially for deployment on **public infrastructures or remote servers**:

- **Minimized port exposure** through Traefik.
- **IP filtering** to restrict service access.
- **Encrypted communications** with automatic SSL certificate management.

## Features

- **Monitor servers and services** via HTTP(s), TCP, Ping, DNS, and more.
- **Customizable notifications** via Telegram, Discord, Email, Slack, and others.
- **Modern and interactive dashboard**.
- **Log storage and failure history tracking**.
- **SSL certificate support via Let's Encrypt with Traefik**.
- **Security-focused setup to minimize exposure risks**.

## Containers

| Name         | Description                               | Port  |
|-------------|-----------------------------------------|------ |
| uptime-kuma | Web interface for service monitoring   | 3001  |

## Security with Traefik

### IP Filtering (Optional)

Traefik allows enabling IP filtering to restrict access to Uptime Kuma.
To enable it, add the authorized IP addresses in the `.env` file under the variable `SERVICE_ALLOWED_IPS`.

Example configuration in `.env`:
```ini
SERVICE_ALLOWED_IPS=192.168.1.1,192.168.1.2
```

If you do not want to enable this restriction, you can comment out or remove these lines in `docker-compose.yml`:
```yaml
- "traefik.http.routers.uptime-kuma.middlewares=uptime-kuma-ipwhitelist,security-headers"
- "traefik.http.middlewares.uptime-kuma-ipwhitelist.ipwhitelist.sourcerange=${SERVICE_ALLOWED_IPS}"
```

### Resource Limitation

The resource limits for the Uptime Kuma container can be defined in the `.env` file:
```ini
UPTIME_KUMA_MEMORY_LIMIT=256M
UPTIME_KUMA_MEMORY_RESERVATION=128M
UPTIME_KUMA_CPU_LIMIT=0.3
```
These values help limit RAM and CPU usage to ensure optimal performance without overloading the server.

## Documentation

For more details on installation and advanced configurations, check out the [Official Uptime Kuma Documentation](https://github.com/louislam/uptime-kuma/wiki).

## Community & Support

- [Community Forum](https://github.com/louislam/uptime-kuma/discussions)
- [GitHub Issues](https://github.com/louislam/uptime-kuma/issues)
