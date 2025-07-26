
# ansible-kubernetes

Ansible Playbook for Automated Kubernetes Installation on Debian

## Overview

This playbook automates the installation and configuration of a Kubernetes cluster on Debian-based systems. It includes tasks for preparing the system, installing required packages, configuring container runtimes, managing GPG keys and repositories, and setting up networking with Flannel.

## Features

- Automated installation of all required APT packages and dependencies
- Secure management of GPG keys and APT repositories
- Configuration of containerd with SystemdCgroup support
- Initialization of the Kubernetes cluster using kubeadm
- Automated setup of kubeconfig for both user and root
- Installation of Flannel as the pod network add-on
- Optional installation of utilities like KubeCTX, KubeNS, and Helm


## Dependencies

Before using this playbook, ensure the following roles are installed:

- [rhattox-ansible/ansible-containerd](https://github.com/rhattox-ansible/ansible-containerd)
- [rhattox-ansible/aansible-containerd-nerdctl](https://github.com/rhattox-ansible/ansible-containerd-nerdctl)

Install these dependencies before running this playbook.

## Prerequisites

- Debian-based system (tested on Debian 10/11)
- Root or sudo privileges
- Swap should be disabled (recommended during Debian installation)

## Playbook Structure

The playbook is organized into roles:

- **pre_install**: Prepares the system, installs basic packages, configures containerd, manages GPG keys, and sets up repositories.
- **core_install**: Installs Kubernetes components, initializes the cluster, and configures networking.

## Example Usage

Run the playbook with:

```bash
ansible-playbook -i inventory main.yaml
```

## Flannel Network Configuration

Default Flannel network variables:

```
FLANNEL_NETWORK=10.244.0.0/16
FLANNEL_SUBNET=10.244.0.1/24
FLANNEL_MTU=1450
FLANNEL_IPMASQ=true
```

You can override these in your inventory or group_vars as needed.

## Notes

This playbook disables swap as part of the installation process if not already done.
