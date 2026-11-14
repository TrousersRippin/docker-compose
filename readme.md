# My Docker-Compose files

This repository contains my personal collection of docker compose YAML files.

## Requirements

Ensure you have Git, Docker and Docker Compose installed on your system.

## Installation

Clone the repo into an empty folder.

Make the required directories for bind mounts.

```bash
mkdir -p /opt/stacks/*
```

## Configuration and secrets

Each stack keeps its non-secret settings directly in the `environment:` block of its `compose.yaml`. Credentials and identifying values (passwords, tokens, domains, URLs, emails) live in a separate `secret.env` file that is gitignored and never committed.

Stacks that need secrets ship a `secret.env.example` with placeholder values. The `env_file: secret.env` line in each compose file has a comment listing the variables it expects.

To set up a stack, copy the example and replace the placeholders with your own values:

```bash
cd gotify
cp secret.env.example secret.env
```

Then edit `secret.env` and start the stack:

```bash
docker compose up -d
```

Stacks without a `secret.env.example` need no secrets and can be started as-is.
