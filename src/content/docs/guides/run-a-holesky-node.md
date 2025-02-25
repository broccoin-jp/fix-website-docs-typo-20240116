---
title: Run a Holesky node
description: This guide will help you get a Holesky archive node up and running.
---

This guide will help you get a Holesky archive node up and running.

## Prerequisites

- [Docker](https://docs.docker.com/engine/install/) is installed and **running**.
- [Git](https://github.com/git-guides/install-git/) is installed.
- If using Windows, you should install [Git BASH](https://gitforwindows.org/) or [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) to use as your terminal.

## Steps

### 1. Clone eth-docker

```bash
git clone https://github.com/eth-educators/eth-docker
cd eth-docker
```

### 2. Do the eth-docker quickstart config

Complete the [eth-docker quickstart](https://eth-docker.net/Usage/QuickStart/). You will need to run the config command:

```bash
./ethd config
```

Make sure to enable Grafana dashboards.

### 3. Expose RPC ports

To expose the node's RPC ports (for a Taiko node to make calls to it), you can append `el-shared.yml` to the list of files in the `COMPOSE_FILE` variable in your `.env` file:

```txt "el-shared.yml"
COMPOSE_FILE=lighthouse-cl-only.yml:geth.yml:el-shared.yml
```

Keep in mind this is **not encrypted**, so you should not expose it to the internet. eth-docker offers a few other options that you can read about [here](https://eth-docker.net/Usage/Advanced#sharing-rpc-and-rest-ports).

### 4. Enable archive node

Also in the `.env` file, set the value `ARCHIVE_NODE` to `true`:

```txt "true"
ARCHIVE_NODE=true
```

### 5. Check your node is running properly

You can visit the [Grafana dashboard](https://eth-docker.net/Usage/Dashboards/#connecting-to-local-grafana) which should be running on `localhost:3000` to verify if your node is running correctly. You should see the chain head increasing.

## Video tutorial

See [Run a Sepolia L1 archive node (YouTube)](https://www.youtube.com/watch?v=7Lg_cY7iP2o), the only difference is you need to select **Holesky testnet**.
