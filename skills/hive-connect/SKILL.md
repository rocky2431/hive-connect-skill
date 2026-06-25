---
name: hive-connect
description: Install Hive Connect, connect this local agent to the user's Hive Local Agent Channel, and keep a cloud-to-local background service online for chat, file transfer, and delegated work.
---

# Hive Connect

Use this skill when the user asks you to install Hive Connect, connect a local agent to Hive, or keep a local agent online for Hive cloud chat and delegated work.

## Goal

Install the `hive-connect` CLI, complete browser-based login, verify the user-scoped Local Agent Channel connection, and install/start the outbound background service.

Login creates a long-lived binding. Do not ask the user to log in again just because the computer slept, restarted, or the service disconnected; restart the background service instead.

## Install The CLI

Run:

```bash
npm install -g @hiveclaw243/hive-connect
hive-connect status
```

If `hive-connect status` says it is not logged in, continue to login.

## Login

Run:

```bash
hive-connect login
```

The browser opens Hive. Let the user log in there. Hive should automatically approve the local agent authentication from the `user_code` in the URL; do not ask the user to copy a code into Hive manually.

For self-hosted or test Hive environments only, ask the user for the Hive URL and run:

```bash
hive-connect login --hive-url <your Hive URL>
```

Then verify:

```bash
hive-connect status
```

## Keep The Local Agent Online

For cloud-to-local chat, file transfer, and delegated work, install and start the background service:

```bash
hive-connect daemon install --config ~/.hive-connect/config.toml --force
hive-connect daemon status
```

This service uses outbound HTTPS/WebSocket connections only. Do not expose a local port, reverse proxy, tunnel, or public callback server.

The background service keeps Hive reachable after the terminal is closed and reconnects after transient WebSocket failures. It streams progress back to Hive before the final result. Treat online/offline as runtime presence only; it is separate from the long-lived login binding.

For foreground debugging only, run:

```bash
hive-connect run
```

## Upload A Local File To Hive

If the installed CLI exposes an upload command, run:

```bash
hive-connect upload <path>
```

If upload is not available, use the Hive Local Agent page's Workspace upload control and report the uploaded workspace path back to the user.
