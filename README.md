# /dev/push images

Base images used by /dev/push runner builds. This repo only contains the base
images (PHP-FPM and FrankenPHP) so local runner builds can reuse layers and
stay fast. Runner images stay in the main devpush repo.

## Publish

1) Push to `main` (or trigger the workflow manually in GitHub Actions).
2) The workflow builds and publishes multi-arch images to GHCR:
   - `ghcr.io/hunvreus/devpush-php-fpm-base:8.3`
   - `ghcr.io/hunvreus/devpush-frankenphp-base:8.3`

The workflow uses `GITHUB_TOKEN` with `packages: write`, so no local token is
required.