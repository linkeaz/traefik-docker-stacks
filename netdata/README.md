<p align="center">
<a href="https://www.netdata.cloud#gh-light-mode-only">
  <img src="https://www.netdata.cloud/img/readme-images/netdata_readme_logo_light.png" alt="Netdata" width="300"/>
</a>
<a href="https://www.netdata.cloud#gh-dark-mode-only">
  <img src="https://www.netdata.cloud/img/readme-images/netdata_readme_logo_dark.png" alt="Netdata" width="300"/>
</a>
</p>

# Netdata

### Author: [Netdata](https://github.com/netdata)
### Repository: [Netdata on GitHub](https://github.com/netdata/netdata)

A real-time monitoring tool to track system and application performance.

## About

Netdata is an **open-source** solution providing real-time monitoring for server, application, and container performance. Its web interface allows interactive visualization of metrics.

## Features

- **Real-time monitoring** of system and application performance.
- **Interactive dashboard** with detailed graphs.
- **Lightweight installation and simple configuration**.
- **Supports alerts and notifications**.
- **Compatible with third-party tools** such as Prometheus, Grafana, InfluxDB, and more.
- **Integration with Traefik** for secure access.

## Containers

| Name     | Description                            | Ports  |
|----------|----------------------------------------|------ |
| netdata  | Real-time monitoring tool             | 19999 |

## IP Filtering and Authentication Configuration

Traefik allows enabling IP filtering to restrict access to Netdata.
To enable it, add the authorized IP addresses in the `.env` file under the variable `ALLOWED_IPS`.

Example configuration in `.env`:
```ini
ALLOWED_IPS=192.168.1.0/24,1.2.3.4
```

If you do not wish to enable this restriction, you can comment out or remove these lines in `docker-compose.yml`:
```yaml
- "traefik.http.routers.netdata.middlewares=netdata-ipwhitelist"
- "traefik.http.middlewares.netdata-ipwhitelist.ipwhitelist.sourcerange=${ALLOWED_IPS}"
```

### Authentication with BasicAuth (Optional)

Netdata can be secured with BasicAuth authentication.
To enable this feature, add a hashed authentication string in the `.env` file under `NETDATA_USERHASH`.

#### Generate a BasicAuth password with `htpasswd`:
```bash
htpasswd -nbB admin MY_PASSWORD
```
This will return a line like:
```plaintext
admin:$2y$05$abc123...
```
Add this value in the `.env` file:
```ini
NETDATA_USERHASH=admin:$2y$05$abc123...
```

Then, ensure the `netdata-auth` middleware is enabled in `docker-compose.yml`:
```yaml
- "traefik.http.routers.netdata.middlewares=netdata-ipwhitelist,netdata-auth"
- "traefik.http.middlewares.netdata-auth.basicauth.users=${NETDATA_USERHASH}"
```

## Documentation

For more details on installation and advanced configurations, check out the [Official Netdata Documentation](https://learn.netdata.cloud/).

## Community & Support

- [Community Forum](https://community.netdata.cloud/)
- [GitHub Issues](https://github.com/netdata/netdata/issues)

