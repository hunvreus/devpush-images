# /dev/push images

High-performance, multi-architecture base images for /dev/push runner builds. 
Optimized for Laravel and modern PHP applications.

## General Features

- **Multi-Arch:** Native support for `linux/amd64` and `linux/arm64` (Apple Silicon/AWS Graviton).
- **Security:** Runs as non-root `appuser` (UID 1000) by default.
- **Performance:** Includes OpCache and JIT configurations optimized for container environments.
- **Tooling:** Composer 2.x included.

## Images

### `ghcr.io/hunvreus/devpush-php-fpm-base:8.3`
- **Engine:** PHP 8.3 FPM (Debian Bookworm)
- **Web Server:** Caddy included (configured to proxy to FPM on port 8000)
- **Extensions:** `bcmath`, `gd`, `intl`, `mbstring`, `opcache`, `pcntl`, `pdo_mysql`, `pdo_pgsql`, `zip`, `redis`
- **Path:** `WORKDIR /app`

### `ghcr.io/hunvreus/devpush-frankenphp-base:8.3`
- **Engine:** FrankenPHP 1 (PHP 8.3)
- **Features:** Optimized for Laravel Octane and worker mode.
- **Extensions:** `bcmath`, `gd`, `intl`, `mbstring`, `opcache`, `pcntl`, `pdo_mysql`, `pdo_pgsql`, `zip`, `redis`
- **Path:** `WORKDIR /app`
