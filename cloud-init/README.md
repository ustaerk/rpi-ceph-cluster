# cloud-init

We use cloud-init to configure the individual nodes at first startup. Make sure to adapt those configs to your setup.

Once we have flashed ubuntu on the SD cards we copy the cloud-init config for the respective node to the boot partition of the card. The cloud-init config doees some basic network configuration as well es ensures that the node has all required packages for our ceph installation as well as user access configured correctly.

## network-config

Configure network settings such as IP addresses and DNS settings.

172.16.0.10 - 172.16.0.29 is reserved for ceph

172.16.0.10 - 172.16.0.14: ceph mon/mgr nodes
172.16.0.15 - 172.16.0.19: ceph osd nodes
172.16.0.29: SMB Gateway

## user-data

Configure packets all nodes should have (e.g. docker.io) as well as basic user setup (user creation, SSH keys, etc.).