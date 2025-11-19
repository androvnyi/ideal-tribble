# Full CI/CD DevOps pipeline using GitLab, Docker, Kubernetes, Prometheus & Grafana.

## Overview
This project demonstrates a **complete DevOps lifecycle** — from code commit to deployment and monitoring — using modern tooling:
- CI/CD via GitLab
- Containerization via Docker
- Deployment via Kubernetes (Minikube)
- Observability via Prometheus & Grafana

The app is a simple **Flask web service** that exposes:
- `/` → returns “Hello from DevOps pipeline!”
- `/health` → for liveness probe
- `/metrics` → Prometheus endpoint for monitoring

---

## Architecture

```mermaid
graph TD;
  Developer[ Developer Push] -->|Git Push| GitLabCI[ GitLab CI/CD];
  GitLabCI -->|Build & Push| Registry[ GitLab Container Registry];
  Registry -->|Deploy| K8s[Kubernetes Cluster];
  K8s -->|Expose| Service[ NodePort Service];
  K8s -->|Monitor| Prometheus[ Prometheus];
  Prometheus --> Grafana[ Grafana Dashboard];
