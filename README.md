# CI/CD Tools and Practices Final Project

This repository contains the completed CI/CD pipeline implementation for the Coursera course **CI/CD Tools and Practices** (IBM DevOps and Software Engineering Professional Certificate).

## Project Overview

In this project, a complete CI/CD pipeline is implemented using GitHub Actions for Continuous Integration and Tekton / Red Hat OpenShift Pipelines for Continuous Delivery. The application is a Flask-based REST microservice with unit testing, linting, containerization, and automated deployment.

## Features & Implementation
- **Continuous Integration (GitHub Actions)**: Automated workflow executing flake8 linting and unit tests via `nosetests` on every push and pull request.
- **Tekton Tasks (`.tekton/tasks.yml`)**: Cloud-native pipeline tasks including workspace cleanup (`cleanup`), linting (`flake8`), and test execution (`nose`).
- **OpenShift Pipelines (`.tekton/pipeline.yaml`)**: End-to-end delivery pipeline orchestrating cleanup, git cloning, linting, unit testing, container image building with Buildah, and Kubernetes deployment.
- **Monitoring & Verification**: Persistent storage via PersistentVolumeClaims (PVC) and deployment logging on OpenShift.

## Setup & Local Testing

Install dependencies:
```bash
bash bin/setup.sh
```

Run linter:
```bash
flake8 service tests --count --max-complexity=10 --max-line-length=127 --statistics
```

Run unit tests:
```bash
nosetests -v --with-spec --spec-color
```

## Repository Structure
- `.github/workflows/workflow.yml` - GitHub Actions CI workflow
- `.tekton/tasks.yml` - Tekton Task definitions (`cleanup` and `nose`)
- `.tekton/pipeline.yaml` - OpenShift Tekton CI/CD Pipeline
- `service/` - Flask REST service source code
- `tests/` - Nose test suites

## Author
Rajnandini (rajnandini15122006@gmail.com)
