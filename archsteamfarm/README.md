# ArchiSteamFarm

## From their [GitHub](https://github.com/JustArchiNET/ArchiSteamFarm)

ArchiSteamFarm (ASF) is a C# application that allows you to farm Steam cards using multiple Steam accounts simultaneously. Unlike other tools, ASF doesn't require a Steam client running in the background and doesn't need any special treatment. It features a built-in web IPC interface for remote management and monitoring.

## Server Ports

| Port | Default | Description |
|------|---------|-------------|
| IPC  | 1242    | Web interface and API (assign as primary) |

## First-Time Setup

Set the `IPC Password` variable before installing to use your own password. If left empty, a random password will be generated and printed to the installation log.

To add Steam accounts, place bot config files (e.g. `MyBot.json`) in the `config/` directory. Refer to the [ASF configuration guide](https://github.com/JustArchiNET/ArchiSteamFarm/wiki/Configuration) for details.

## Variables

| Variable        | Default   | Description                                                       |
|-----------------|-----------|-------------------------------------------------------------------|
| `ASF_VERSION`   | `latest`  | ASF version to install (`latest` or a tag like `6.0.0.3`)        |
| `IPC_PASSWORD`  | _(empty)_ | IPC web interface password. Leave empty to generate a random one. |
| `ASF_URL`       | _(empty)_ | Override download URL (leave empty to use GitHub releases)        |
| `ASF_ARGS`      | _(empty)_ | Extra command-line arguments passed to ASF on startup             |

## Notes

- Reinstalling the server regenerates `config/ASF.json`. If you used a random password and did not note it down, reinstalling is the easiest way to reset it.
- Bot config files placed in the `config/` directory are preserved between restarts and reinstalls.
