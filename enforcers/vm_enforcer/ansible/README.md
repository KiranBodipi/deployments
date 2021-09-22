# Deploy VM Enforcer using Ansibel Playbook

## Overview

You can deploy VM Enforcers, using an Ansible playbook, on the desired VM Enforcer group. This procedure is supported for Linux platforms only.

## Prerequisites for deploying VM Enforcers

* VM Enforcer Group token. Refer to [Create a VM Enforcer Group and VM Enforcer](https://docs.aquasec.com/docs/create-a-vm-enforcer-group-and-vm-enforcer) to create this token.
* Aqua username and password
* Following packages are required on the VM to install VM Enforcer:
   * jq
   * runc
   * tar
   * wget

## Preparation

**Step 1. Download the Ansible playbook**

```shell
git clone https://github.com/aquasecurity/deployments.git -b 6.5
cd ./deployments/enforcers/vm_enforcer/ansible/
```

**Step 2. Create a `hosts` file with the IP or DNS addresses of the VM(s).** For example:

```bash
[all]     # list the IP/DNS addresses of the VMs to deploy VM Enforcer
10.0.0.1 
10.0.0.x
test.aqua.com
```

## Deploy VM Enforcer

Add the [mandatory variables](#mandatory-variables) with the `--extra-vars` flag in the deployment command as shown below, and run the command.

```shell
ansible-playbook vm-enforcer.yaml -i ./path/to/hosts -e vme_install=true --extra-vars "USERNAME=<username> PASSWORD=<password> ENFORCER_VERSION=<version> TOKEN=<token> GATEWAY_ENDPOINT=<endpoint>:<port>"
```

## References
* Getting started with [Ansible](https://docs.ansible.com/ansible/latest/user_guide/intro_getting_started.html) and [Run your first Playbook](https://docs.ansible.com/ansible/latest/network/getting_started/first_playbook.html) guides.
* [Aqua VM Enforcer Overview](../README.md) and all other [Aqua Enforcers types](../../README.md) overview
* Aqua VM Enforcers [official documentation](https://docs.aquasec.com/docs/vm-enforcer)