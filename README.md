# valheim-community-scripts

Runs a Valheim dedicated server in a Proxmox VE LXC. Written for
[community-scripts/ProxmoxVED](https://github.com/community-scripts/ProxmoxVED).

* `ct/valheim.sh` creates the container and handles updates. Worlds are backed
  up before each update and restored if SteamCMD fails.
* `install/valheim-install.sh` installs SteamCMD and the server, sets up a
  systemd unit, and writes settings to `/opt/valheim/valheim.env`.
* `json/valheim.json` holds metadata for the community-scripts site.

Run on a Proxmox host:

```bash
bash ct/valheim.sh
```

For unattended installs, set `var_server_name`, `var_world_name`,
`var_server_password` (min 5 chars) and `var_crossplay` before running.

Defaults to Debian 13, unprivileged, 2 cores, 4 GB RAM, 10 GB disk.
The game uses UDP ports 2456-2457. x86_64 only.
