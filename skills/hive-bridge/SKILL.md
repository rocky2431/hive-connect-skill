---
name: hive-bridge
description: Compatibility alias for Hive Connect. Install and use Hive Connect for the Hive Local Agent Channel.
---

# Hive Bridge Compatibility Alias

Hive Bridge has been renamed to Hive Connect.

For any user request that mentions Hive Bridge, use the `hive-connect` flow instead:

```bash
npm install -g @hiveclaw243/hive-connect
hive-connect login
hive-connect status
hive-connect daemon install --config ~/.hive-connect/config.toml --force
hive-connect daemon status
```

`hive-connect status` checks the saved login binding. `hive-connect daemon status` checks the background service. If Hive shows the local agent offline but the machine is still logged in, restart or reinstall the daemon instead of creating a new login binding.

Do not install the old bridge package for new users.
