# FastAPI Project Setup

A reproducible FastAPI project using Python 3.12+, `uv`, Uvicorn, Docker, and Docker Compose.

## Features

- FastAPI application with a health-check endpoint
- Dependency management and lockfile using `uv`
- Python source code organized under `src/`
- Docker container for consistent execution
- Docker Compose with hot reload for development

## Requirements

For local development:
- Python 3.12+
- `uv`

For containerized development:
- Docker Desktop
- Docker Compose

## Project Structure

```text
fastapi-project-setup/
├── src/
│   └── fastapi_project_setup/
│       ├── __init__.py
│       └── main.py
├── .env.example
├── .gitignore
├── .python-version
├── Dockerfile
├── compose.yaml
├── pyproject.toml
├── uv.lock
└── README.md
```

- `src/fastapi_project_setup/main.py`: FastAPI application and health endpoint.
- `pyproject.toml`: Project metadata, Python requirement, and dependencies.
- `uv.lock`: Locked dependency versions for reproducible installation.
- `Dockerfile`: Instructions for building the API image.
- `compose.yaml`: Container configuration and development hot reload.
- `.env.example`: Example environment configuration.

## Local Setup

Clone the repository and enter the project directory:

```bash
git clone https://github.com/ItsWaqasTariq/fastapi-project-setup.git
cd fastapi-project-setup
```

Install the locked dependencies:

```bash
uv sync --locked
```

Start the development server:

```bash
uv run uvicorn fastapi_project_setup.main:app --reload
```

Open the health endpoint:

http://127.0.0.1:8000/health

Interactive API documentation:

http://127.0.0.1:8000/docs

## Docker Setup

Build and start the API:

```bash
docker compose up --build
```

Open http://127.0.0.1:8000/health to check the service.

Run in the background:

```bash
docker compose up -d
```

Check container status:

```bash
docker compose ps
```

Stop the service:

```bash
docker compose down
```

The Compose configuration mounts the source directory and enables Uvicorn reload for development.

## Health Endpoint

**Request:** `GET /health`

**Successful response:** HTTP 200

```json
{
  "status": "ok",
  "version": "0.1.0"
}
```

## Environment and Secrets

Copy `.env.example` to `.env` if local environment variables are needed. Never commit real secrets or `.env` files. The `.venv` directory and generated caches are excluded through `.gitignore`.

## Verification

The following checks have been performed during development:

- [x] Local health endpoint returns HTTP 200 and valid JSON.
- [x] Dependencies synchronize using `uv sync --locked`.
- [x] Docker image builds successfully.
- [x] Docker Compose starts the API.
- [x] Health endpoint returns HTTP 200 inside Docker.
- [x] API responds after restarting the container.

## Development Branch

`task/01-project-setup`

This branch contains the initial project skeleton and local development environment configuration.