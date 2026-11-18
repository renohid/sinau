# Containerized Python CI/CD Pipeline

![CI/CD Pipeline](https://github.com/renohid/sinau/actions/workflows/ci-cd.yaml/badge.svg)

Automated CI/CD pipeline built with **GitHub Actions**, **Pytest**, and **Docker**.

## Pipeline Architecture
1. **Quality Gate (`test`):** Runs on every push and pull request to `main` using an isolated Ubuntu runner, caches `pip` dependencies, and executes unit tests via `pytest`.
2. **Container Build & Delivery (`build-and-push`):** Triggered only after `test` passes on `main`. Authenticates to Docker Hub via encrypted repository secrets and pushes a `linux/amd64` image tagged with both `latest` and the immutable `github.sha`.

## Run the Published Image

**Linux / Windows (`amd64`):**
```bash
docker pull renohid/my-app:latest
docker run --rm renohid/my-app:latest

```
**MacOS (`amd64`):**
```bash
docker pull --platform linux/amd64 renohid/my-app:latest
docker run --rm --platform linux/amd64 renohid/my-app:latest


