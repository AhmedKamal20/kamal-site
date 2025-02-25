---
title: Hooks
---

# Hooks

You can run custom scripts at specific points with hooks.

Hooks should be stored in the **.kamal/hooks** folder. Running `kamal init` will build that folder and add some sample scripts.

You can change their location by setting `hooks_path` in the configuration file.

If the script returns a non-zero exit code the command will be aborted.

`KAMAL_*` environment variables are available to the hooks command for fine-grained audit reporting, e.g. for triggering deployment reports or firing a JSON webhook. These variables include:

- `KAMAL_RECORDED_AT` — UTC timestamp in ISO 8601 format, e.g. `2023-04-14T17:07:31Z`
- `KAMAL_PERFORMER` — The local user performing the command (from `whoami`)
- `KAMAL_SERVICE_VERSION` — An abbreviated service and version for use in messages, e.g. app@150b24f
- `KAMAL_VERSION` — The full version being deployed
- `KAMAL_HOSTS` — A comma-separated list of the hosts targeted by the command
- `KAMAL_COMMAND` — The command we are running
- `KAMAL_SUBCOMMAND` — *Optional:* The subcommand we are running
- `KAMAL_DESTINATION` — *Optional:* Destination, e.g. "staging"
- `KAMAL_ROLE` — *Optional:* Role targeted, e.g. "web"

The available hooks are
- [docker-setup](../docker-setup)
- [pre-connect](../pre-connect)
- [pre-build](../pre-build)
- [pre-deploy](../pre-deploy)
- [post-deploy](../post-deploy)
- [pre-traefik-reboot](../pre-traefik-reboot)
- [post-traefik-reboot](../post-traefik-reboot)

You can pass `--skip_hooks` to avoid running the hooks.
