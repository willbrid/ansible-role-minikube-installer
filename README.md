# Ansible-role-minikube-installer

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/willbrid/ansible-role-minikube-installer/blob/main/LICENSE) [![CI](https://github.com/willbrid/ansible-role-minikube-installer/actions/workflows/ci.yml/badge.svg)](https://github.com/willbrid/ansible-role-minikube-installer/actions/workflows/ci.yml)

Le rôle **ansible-role-minikube-installer** permet d’installer **Minikube** sur un système Linux (distributions RedHat et Debian), en tenant compte de l’architecture matérielle (comme amd64, arm64, etc.). Il automatise le téléchargement binaire de la version spécifiée et configure **Minikube** pour une utilisation immédiate.

## Exigences

Système Linux.

## Description des Variables

|Nom|Type|Description|Obligatoire|Valeur par défaut|
|---|----|-----------|-----------|-----------------|
`minikube_version`|str|numéro de version de minikube. Format : vx.y.z|non|`"v1.35.0"`
`minikube_bin_dir`|str|répertoire d'installation du binaire de minikube|non|`"/usr/local/bin`
`should_verify_minikube_checksum`|bool|dire s'il faut vérifier l'intégrité du fichier binaire de minikube après téléchargement|non|`true`

## Dépendances

Aucune.

## Exemple Playbook

- Installation du rôle

```bash
mkdir -p $HOME/install-minikube/roles
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
cd $HOME/install-minikube && ansible-galaxy install -r requirements.yml --roles-path roles
```

- Utilisation du rôle dans un playbook

```bash
vim $HOME/install-minikube/playbook.yml
```

```yaml
---
- hosts: localhost
  vars:
    minikube_version: "v1.35.0"
    should_verify_minikube_checksum: true

  roles:
    - ansible-role-minikube-installer
```

```bash
cd $HOME/install-minikube && ansible-playbook playbook.yml
```

## Licence

MIT

## Informations sur l'auteur

William Bridge NGASSAM
