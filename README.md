# Ansible-role-minikube-installer

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/willbrid/ansible-role-minikube-installer/blob/main/LICENSE) [![CI](https://github.com/willbrid/ansible-role-minikube-installer/actions/workflows/ci.yml/badge.svg)](https://github.com/willbrid/ansible-role-minikube-installer/actions/workflows/ci.yml)

The **ansible-role-minikube-installer** role allows you to install **Minikube** on a Linux system (Red Hat and Debian distributions), taking into account the hardware architecture (such as amd64, arm64, etc.). It automates the binary download of the specified version and configures **Minikube** for immediate use.

## Requirements

- Linux systems: Red Hat and Debian distributions

## Description of Variables

|Name|Type|Description|Mandatory|Default value|
|--- |----|-----------|---------|-------------|
`minikube_version`|str|Minikube version number. Format: vx.y.z|no|`"v1.35.0"`
`minikube_bin_dir`|str|minikube binary installation directory|no|`"/usr/local/bin"`
`should_verify_minikube_checksum`|bool|specify whether the integrity of the minikube binary file should be checked after downloading|no|`true`

## Dependencies

None.

## Example Playbook

- Role installation

```bash
mkdir -p $HOME/install-minikube
```

```bash
vim $HOME/install-minikube/requirements.yml
```

```yaml
- name: ansible-role-minikube-installer
  src: git+https://github.com/willbrid/ansible-role-minikube-installer.git
  version: v1.0.0
```

```bash
cd $HOME/install-minikube && ansible-galaxy install --force -r requirements.yml
```

- Using the role in a playbook

```bash
vim $HOME/install-minikube/playbook.yml
```

```yaml
---
- hosts: localhost
  become: true

  vars:
    minikube_version: "v1.35.0"
    should_verify_minikube_checksum: true

  roles:
    - ansible-role-minikube-installer
```

```bash
cd $HOME/install-minikube && ansible-playbook playbook.yml
```

## License

MIT

## Author Information

William Bridge NGASSAM
