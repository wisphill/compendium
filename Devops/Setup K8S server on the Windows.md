#wsl
### Install WSL and SSH access from MAC

1. Install WSL Ubuntu 24.04 on the Windows machine
2. Update policy on the Windows to allow port forwarding for the port 22 from Windows to the WSL and set up the SSH server on the WSL
3. On the Windows, enable the task scheduler to auto start the WSL whenever booting the Windows. WSL requires some processes to be run in the background to prevent auto shutdown, just make sure the task scheduler has some options to handle this.
4. Install the `tailscale` VPN peering to peer to access/ssh WSL from the different network. Allow all ports from dst and src at the tailscale for easy access.


### Install K8S server
```
### WSL to disable swap for the K8S to ensure the resource guarantees
sudo swapoff -a
sed -i '/ swap / s/^/#/' /etc/fstab

### Install K3S
curl -sfL https://get.k3s.io | sh -

```

### IP tables
```
1. Install the iptables and iptables-persistent to access the ip tables file and dump the file, and access the net filter configurations.
```

## Other installations
-  Install cloudflared in WSL for tunneling to the Cloudflare & started as service. Cloudflared service requires root permission to run
