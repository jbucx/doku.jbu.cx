---
title: How to enable VNC on Proxmox
date: 2023-03-06 03:30:00 +100
categories: []
tags: [proxmox,vnc]     # TAG names should always be lowercase
---

1. Shut the VM down
2. Edit the configuration file in `/etc/pve/qemu-server/VMID.conf`
3. To get the port, you need to select a port above 5900 and subtract 5900 from it. So if I want my VNC Server for that VM to listen on port 5959, I need to write `:59` as a port in the config.
4. Add this to the config, if you want the VNC Server to listen on IPv6
```bash
args: -vnc [::]:59
```
    1. or this config, if you want the VNC Server to listen on Legacy-IP (IPv4)
    ```bash
    args: -vnc 0.0.0.0:59
    ```
5. Start the VM
6. You should now be able to control the VM via VNC