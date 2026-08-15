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

## Runpod MCP server

This project was deployed and managed with the official
[Runpod MCP server](https://github.com/runpod/runpod-mcp). It gives compatible
AI tools a structured interface for managing Runpod Pods, Serverless endpoints,
templates, network volumes, registries, and related infrastructure.

For this deployment, the MCP server was used to check Secure Cloud GPU
availability and pricing, create the Pod, inspect its status and logs, and
terminate it when the demo was complete. The application was exposed through
Runpod's HTTPS proxy without storing a Runpod API key in this repository.

See Runpod's [MCP server guide](https://docs.runpod.io/get-started/mcp-servers)
for hosted and local setup options. The upstream project also provides a guided
installer:

```bash
npx @runpod/mcp-server@latest add
```

## How it was created

This page was created from a simple prompt: build a developer-first “hello”
application and deploy it on a secure Runpod pod. Follow-up prompting refined
the cloud label, security settings, deployment cost, and repository packaging.

The MCP workflow kept infrastructure actions conversational and auditable while
the application itself remained plain HTML, CSS, and JavaScript.
