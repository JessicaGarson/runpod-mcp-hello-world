# Secure RunPod Hello World

A developer-focused Hello World application deployed on a RunPod Secure Cloud
Pod. It uses a small nginx Alpine image, a responsive terminal-inspired page,
and a JSON health endpoint.

## Live deployment

- Application: <https://si7x2rbbb49xcf-8080.proxy.runpod.net/>
- Health: <https://si7x2rbbb49xcf-8080.proxy.runpod.net/status>
- Pod ID: `si7x2rbbb49xcf`
- Cloud: RunPod Secure Cloud
- Port: `8080/http`

The live Pod incurs usage charges until it is stopped or terminated.

## Run locally

```bash
docker build -t runpod-mcp-hello-world .
docker run --rm -p 8080:8080 runpod-mcp-hello-world
```

Open <http://localhost:8080>. Check the service with:

```bash
curl http://localhost:8080/status
```

Expected response:

```json
{"message":"Hello, World!","runtime":"RunPod Secure Cloud","status":"healthy"}
```

## Security

The deployment uses RunPod Secure Cloud and exposes only the HTTP application
port through RunPod's HTTPS proxy. nginx disables version tokens and returns a
Content Security Policy, `X-Content-Type-Options`, `X-Frame-Options`, and a
no-referrer policy. No credentials or RunPod API keys are stored in this repo.

## RunPod deployment

The Pod was created through the official
[RunPod MCP server](https://github.com/runpod/runpod-mcp) using the reusable
template `7wht0klf7n`. The current Pod uses one NVIDIA RTX 2000 Ada Generation
GPU and a 5 GB container disk.
