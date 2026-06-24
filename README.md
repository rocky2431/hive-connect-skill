# Hive Connect Skill Package

This repository is the Skills CLI entrypoint for installing the Hive Connect skill into local agent tools.

## Install

Install the skill:

```bash
npx skills add https://github.com/rocky2431/hive-connect-skill --skill hive-connect
```

If your agent supports global skill installation and you want the Skills CLI to target detected agents:

```bash
npx skills add https://github.com/rocky2431/hive-connect-skill --skill hive-connect -g
```

## What This Installs

The Skills CLI installs only the `hive-connect` skill instructions. The skill then guides the local agent to install and operate the CLI:

```bash
npm install -g @hiveclaw243/hive-connect
hive-connect login --hive-url <Hive URL copied from Hive>
hive-connect status
hive-connect run
```

The npm package is the executable local runner. This GitHub repository is the agent skill package.

`hive-connect login` creates a long-lived binding. `hive-connect run` is the online runner: it keeps one outbound WebSocket session open for consecutive cloud messages, streams progress back to Hive, and reconnects after transient WebSocket failures.

## Compatibility

The old `hive-bridge` skill name remains as a compatibility alias, but new installations should use `hive-connect`.
