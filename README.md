# ansible-kubernetes
Ansible Script to help kubernetes installation on Debian

## Notes:

This installation doesn't require Swap, because, it has been disabled during debian installation.

## Order:

1. main
2. addons
3. init
4. install_network

```
FLANNEL_NETWORK=10.244.0.0/16
FLANNEL_SUBNET=10.244.0.1/24
FLANNEL_MTU=1450
FLANNEL_IPMASQ=true
```
