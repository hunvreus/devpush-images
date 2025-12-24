# devpush-images

Base images used by Devpush runner builds. This repo only contains the base
images (PHP-FPM and FrankenPHP) so local runner builds can reuse layers and
stay fast. Runner images stay in the main devpush repo.

## Layout

- `docker/Dockerfile.php-fpm-base-8.3`
- `docker/Dockerfile.frankenphp-base-8.3`

## Local build

Build both bases first:

```sh
docker build -f docker/Dockerfile.php-fpm-base-8.3 \
  -t devpush-php-fpm-base:8.3 docker

docker build -f docker/Dockerfile.frankenphp-base-8.3 \
  -t devpush-frankenphp-base:8.3 docker
```

## Publish to GHCR (multi-arch)

Create a buildx builder once:

```sh
docker buildx create --name devpush-builder --use
```

Build and push:

```sh
docker buildx build --platform linux/amd64,linux/arm64 \
  -t ghcr.io/<org>/devpush-php-fpm-base:8.3 --push \
  -f docker/Dockerfile.php-fpm-base-8.3 docker

docker buildx build --platform linux/amd64,linux/arm64 \
  -t ghcr.io/<org>/devpush-frankenphp-base:8.3 --push \
  -f docker/Dockerfile.frankenphp-base-8.3 docker
```

## Using in Devpush

In the main repo, update runner Dockerfiles to `FROM devpush-php-fpm-base:8.3`
/ `devpush-frankenphp-base:8.3` (local) or the GHCR tags (remote).
