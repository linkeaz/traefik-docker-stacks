# 🐳 Traefik and Docker Stacks

[![CC BY-SA 4.0][cc-by-sa-shield]][cc-by-sa]
![Docker](https://img.shields.io/badge/-Docker_compose-2496ED?style=flat&logo=docker&logoColor=white)
![Traefik](https://img.shields.io/badge/-Traefik_Proxy-24A1C1?style=flat&logo=traefikproxy&logoColor=white)


This collection of **Docker Compose** stacks allows for easy self-hosting using **Traefik** as the main reverse proxy. It automatically manages SSL certificates and ensures secure routing.

---

## 📂 Project Structure

```
dockge/
├── .env.example
├── README.md
├── docker-compose.yml
traefik/
├── .env.example
├── README.md
├── docker-compose.yml
.../
CODE_OF_CONDUCT.md
LICENSE
README.md (this file)
```

Each Docker service is organized into its own subdirectory with its respective `docker-compose.yml` file.

---

## 💡 Project Overview

This project provides a collection of **secure Docker Compose stacks**, designed for reliable deployment on **public infrastructures, remote servers, and security-sensitive environments**. Each configuration is optimized to **minimize port exposure**, **encrypt communications**, and **restrict access to sensitive interfaces**.

It simplifies self-hosting by ensuring **secure routing** and **automated SSL certificate management** via Let's Encrypt.

### Features and Security:

- **Traefik** as a reverse proxy to centralize and secure service access.
- **Automated SSL certificate management** with Let's Encrypt.
- **Dockge** for graphical management of Docker stacks.
- **IP filtering and authentication** to restrict access to sensitive interfaces.
- **Minimal port exposure** to reduce the attack surface.
- **Encrypted communications** and adherence to security best practices.
- **Modular organization** allowing easy integration of new services.

---

## 🏗 **Traefik** (Secure Reverse Proxy)

- Intelligent routing for HTTP/HTTPS requests.
- Automated SSL certificate management.
- Service security with middlewares (authentication, IP filtering, etc.).

### **Other Modular Services**

This project is designed to be **scalable**, allowing additional services to be integrated into Traefik with custom configurations.

---

## ⚙️ Configuration and Customization

Each stack offers different configuration methods depending on usage:

- **Via `.env` files**: Some services use environment variables stored in a `.env` file.
- **Via `docker-compose.yml`**: Main configurations are directly within this file.
- **Customization during installation**: Some parameters must be manually set before deployment.

### Configuration Examples

- **Secure Access**: Add authentication or restrict access via Traefik middlewares.
- **SSL Certificates**: Let's Encrypt automatically generates certificates; ensure your DNS is correctly set up before deployment.

---

## 📖 Useful Resources

- [Traefik Documentation](https://doc.traefik.io/traefik/)
- [Docker Docs](https://docs.docker.com/)
- [Let’s Encrypt](https://letsencrypt.org/docs/)

---

## © License & Attribution

This project is licensed under the [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).

[![CC BY-SA 4.0][cc-by-sa-image]][cc-by-sa]

### Rights and Obligations:

-  You may **use, modify, and redistribute** this guide and its configurations.
-  You must **credit the author** by citing **[Linkeaz](https://github.com/linkeaz)** or [Slym B.](https://github.com/slymb).
-  You **may not remove attribution**.


[cc-by-sa]: http://creativecommons.org/licenses/by-sa/4.0/
[cc-by-sa-image]: https://licensebuttons.net/l/by-sa/4.0/88x31.png
[cc-by-sa-shield]: https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg


