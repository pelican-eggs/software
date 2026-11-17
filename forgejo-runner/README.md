# Forgejo Runner Pelican Egg

This Pelican egg allows you to run a [Forgejo Actions Runner](https://code.forgejo.org/forgejo/runner) inside a Pelican panel container. It automates the download, configuration, and registration of the runner with your Forgejo instance.

## Features

- Automatic download and setup of the official Forgejo Runner binary.
- Configurable environment variables for seamless instance integration.
- Automatically generates and sets up the required configuration and registration files.

## Variables

When creating a server using this egg, you can configure the following environment variables:

| Variable | Description | Default / Example | Required |
| :--- | :--- | :--- | :--- |
| **Forgejo URL** | Full URL of your Forgejo instance | `https://git.example.com` | Yes |
| **Runner Name** | Name of the runner displayed in Forgejo | `pelican-runner` | Yes |
| **Runner Token** | Registration token provided by your Forgejo instance | *None* | Yes |
| **Runner UUID** | Unique identifier generated for the runner | *None* | Yes |

## Getting Started

1. Create a new runner in your Forgejo instance (Site Administration -> Actions -> Runners -> Create new runner).
2. Copy the generated **Token** and **UUID**.
3. Create a new server in Pelican using this egg.
4. Fill in your **Forgejo URL**, **Runner Name**, **Runner Token**, and **Runner UUID** in the startup variables.
5. Start the server! The installation script will automatically register and start the daemon.

## Ports

This daemon does not expose any web or SSH ports by default as it communicates via outgoing requests to your Forgejo instance.
