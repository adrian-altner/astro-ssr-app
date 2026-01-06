# Docker Publish Workflow (GHCR)

## What it does
The GitHub Actions workflow at `.github/workflows/docker-publish.yml` builds a multi-arch Docker image (`linux/amd64`, `linux/arm64`) and pushes it to GitHub Container Registry (GHCR).

## When it runs
- Trigger: pushing a Git tag that matches `v*` (examples: `v0.1.0`, `v1.2.3`).

## Image name and tags
Images are published as:
- `ghcr.io/<OWNER>/<REPO>:<TAG>` (e.g., `ghcr.io/adrian-altner/astro-ssr-app:v0.1.1`)
- `ghcr.io/<OWNER>/<REPO>:latest`

## How to cut a release
1) Make sure the `Dockerfile` is committed to the default branch:
- `git add Dockerfile .dockerignore .github/workflows/docker-publish.yml`
- `git commit -m "Add Docker publish workflow"`
- `git push origin main`

2) Create and push a release tag:
- `git tag -a v0.1.1 -m "Release v0.1.1"`
- `git push origin v0.1.1`

## Where to find the published image
- Repository page → **Packages** → container package for this repo.
- Direct URL pattern: `https://github.com/<OWNER>/<REPO>/pkgs/container/<REPO>`

## Pulling the image locally
If the package is private, authenticate first:
- `echo "$GITHUB_TOKEN" | docker login ghcr.io -u <USERNAME> --password-stdin`

Then pull/run:
- `docker pull ghcr.io/<OWNER>/<REPO>:v0.1.1`
- `docker run --rm -p 4321:4321 ghcr.io/<OWNER>/<REPO>:v0.1.1`
