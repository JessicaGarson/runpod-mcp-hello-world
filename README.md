# Secure Runpod Hello

A zero-dependency, developer-first hello page built for a Runpod Secure Cloud
pod. The interface uses a terminal-inspired layout, responsive styling, and a
small vanilla JavaScript runtime clock.

## Run locally

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Run in a container

```bash
docker run --rm -p 8000:80 \
  -v "$PWD/index.html:/usr/share/nginx/html/index.html:ro" \
  nginx:alpine
```

The original deployment exposed only its HTTP application port through
Runpod's HTTPS proxy. The pod itself has been terminated, so this repository is
the durable source for the application.

## How it was created

This page was created from a simple prompt: build a developer-first “hello”
application and deploy it on a secure Runpod pod. Follow-up prompting refined
the cloud label, security settings, deployment cost, and repository packaging.

The Runpod MCP server handled infrastructure operations directly: checking GPU
availability and pricing, launching the Secure Cloud pod, inspecting its status
and logs, verifying the deployment, and terminating the pod afterward. No API
keys or other credentials are stored in this repository.
