# syntaxnow-assets

Centralized static asset service for the Syntaxnow platform.

This repository builds a lightweight NGINX-based Docker image that serves
shared UI assets such as:

- Argo CD custom CSS
- Platform branding (SVG logos, favicons)
- Future: Keycloak, Grafana, docs theming assets

The service is deployed via GitOps and exposed over HTTPS.

---

# Local Development & Testing
## Option 1: Simple local HTTP server (no Docker)
```sh
cd assets
python3 -m http.server 8080
```
open
```text
http://localhost:8080
```
## Option 2: Docker (production-equivalent)
Build the image:
```sh
docker build -t syntaxnow-assets:local .
```
Run it:
```sh
docker run --rm -p 8080:80 syntaxnow-assets:local
```
Open
```text
http://localhost:8080
http://localhost:8080/css/argo/argo-custom.css
http://localhost:8080/branding/logo-full.svg
```
## Repository Structure

```text
syntaxnow-assets
├── assets
│   ├── index.html              # Local test page
│   ├── css
│   │   └── argo
│   │       └── argo-custom.css # Argo CD UI overrides
│   └── branding
│       ├── logo-full.svg
│       ├── light/
│       └── dark/
├── Dockerfile
├── .dockerignore
├── .gitignore
└── README.md
