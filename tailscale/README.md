# [Tailscale](https://github.com/tailscale/tailscale)

Tailscale is a simple VPN that securely connects your devices, letting you access your local network from anywhere.

## Features
- **Exit Node Support**: Route all network traffic through this server.
- **Subnet Routing**: Securely access your local network (e.g., `192.168.1.0/24`) from anywhere.

## Host Requirements

For Exit Node and Subnet Routing, IP forwarding must be enabled on the host system.

1. **Configure IP Forwarding:**

   Add or modify the following lines in `/etc/sysctl.conf`:

   ```bash
   net.ipv4.ip_forward=1
   net.ipv6.conf.all.forwarding=1
   ```

**Note for systems without `/etc/sysctl.conf`:**
Some distributions do not include this file by default. In this case, create a new configuration file in the appropriate directory (e.g., `/etc/sysctl.d/99-ipforward.conf`) and add the lines listed above.

2. **Apply the changes:**

   If you edited `/etc/sysctl.conf`:
   ```bash
   sudo sysctl -p
   ```
   If you created a new file in `/etc/sysctl.d/`:
   ```bash
   sudo sysctl --system
   ```

## Configuration
1. Generate an access token:
- Go to https://login.tailscale.com/admin/settings/keys
- Click "Generate New Key"
- Copy the token and set it as TAILSCALE_AUTH_KEY

2. After the server starts, manually approve the Exit Node/Subnet Routes in the Tailscale Admin Console: https://login.tailscale.com/admin/machines
