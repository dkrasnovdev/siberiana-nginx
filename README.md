<p align="center">
  <picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/dkrasnovdev/siberiana-public-assets/main/assets/siberiana-logo-dark-background.svg">
  <img src="https://raw.githubusercontent.com/dkrasnovdev/siberiana-public-assets/main/assets/siberiana-logo-dark-background.svg" width="240" height="90" alt="Logo for Siberiana">
</picture>
</p>

<p align="center">
Siberiana | Aggregator of the Historical and Cultural Heritage of the Yenisei Siberia.
</p>

# Siberiana NGINX Setup

This repository contains configuration files and instructions for setting up NGINX with Let's Encrypt SSL certificates for your Siberiana project.

## Prerequisites

Before you begin, ensure you have the following installed:

- Docker
- Docker Compose

## Getting Started

1. Clone this repository to your local machine:

   ```bash
   git clone https://github.com/dkrasnovdev/siberiana-nginx.git
   cd siberiana-nginx
   ```

2. Edit the `init-letencrypt.sh` script:

   Open the `init-letencrypt.sh` script and set the following values:

   - `domains`: Add your main domain and subdomains (api.<domain>, oauth.<domain>, s3.<domain>, console.<domain>).
   - `staging`: Set to `1` for initial testing and certificate generation, then change to `0` for actual certificates.

   Run the following commands to make the script executable and then execute it:

   ```bash
   chmod +x init-letencrypt.sh
   ./init-letencrypt.sh
   ```

3. Edit `conf.d/app.conf`:

   Uncomment the HTTPS server blocks and upstream sections. Replace `<domain>` with your actual domain and `<container_name>:<container_port>` with your container information.

4. Restart NGINX:

   ```bash
   docker-compose restart nginx
   ```

5. Access Your Project:

   Your project should now be accessible at your domain and subdomains with HTTPS.

## Files

- `init-letencrypt.sh`: Script to initialize Let's Encrypt certificates and configure NGINX.
- `docker-compose.yml`: Docker Compose configuration for NGINX and Certbot services.
- `conf.d/app.conf`: NGINX configuration for handling different subdomains and SSL termination.

## Customization

You can customize the NGINX configuration in `conf.d/app.conf` to suit your project's specific requirements.

## Troubleshooting

If you encounter any issues or have questions, please feel free to create an issue on this repository.
