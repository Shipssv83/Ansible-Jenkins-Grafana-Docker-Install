Hi, ![](https://user-images.githubusercontent.com/18350557/176309783-0785949b-9127-417c-8b55-ab5a4333674e.gif)my name is Serhii Shypylov
=========================================================================================================================================

-------------------------------

### Socials

<p align="left"> <a href="https://github.com/Shipssv83" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github.svg" width="32" height="32" /> </picture> </a> <a href="https://www.linkedin.com/in/sergey-shipilov-7262a31b4/" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin.svg" width="32" height="32" /> </picture> </a></p>
---

# Server Installation Playbook

This Ansible playbook is designed to set up and configure servers in a production environment. It includes setting up the timezone, installing essential services, configuring NTP with Chrony, securing the server with SSH and UFW, and more.

---

## Playbook Overview

The playbook performs the following tasks:

- **Server Setup**: Basic configuration including setting up the timezone and essential services.
- **Chrony NTP Setup**: Configures the Chrony service for network time synchronization.
- **SSH Configuration**: Sets up the SSH daemon according to security best practices.
- **UFW Firewall Configuration**: Configures the UFW firewall to secure the server.

---

## Requirements

- **Ansible 2.9+** installed on the control node.
- **SSH access** to the target hosts.
- The target hosts should be running a Unix-based operating system (e.g., Ubuntu, RHEL).

---

## Roles and Playbooks

### Roles
- `server-install`: Performs the basic server setup.
- `frzk.chrony`: Configures Chrony for NTP synchronization.

### Included Playbooks
- `sshd.yml`: Configures the SSH daemon (included in the main playbook).
- `ufw.yml`: Configures the UFW firewall (included in the main playbook).

---

## Variables

You can define the following variables to customize the playbook:

### Global Variables
- `hosts`: Target hosts where the playbook will be applied.
- `env`: Environment (default: `prod`).
- `env_color`: Color code for environment output (default: `033[0;33m`).
- `timezone`: The timezone to be set on the server (default: `Europe/Warsaw`).

### Chrony Variables
These variables are used to configure Chrony for NTP synchronization:

- `chrony_service_name`: Name of the Chrony service (default: `chronyd`).
- `chrony_ntp_pools`: List of NTP pools to use (empty by default).
- `chrony_ntp_servers`: List of NTP servers to use (default: RHEL NTP pool).
- `chrony_config_file`: Path to the Chrony configuration file (default: `/etc/chrony.conf`).
- `chrony_config_driftfile`: Drift file for Chrony (default: `/var/lib/chrony/drift`).
- `chrony_config_logdir`: Directory for Chrony logs (default: `/var/log/chrony`).
- `chrony_makestep_threshold`: Threshold for time correction (default: `5`).
- `chrony_makestep_limit`: Maximum time correction limit (default: `3`).

---

## Ansible Galaxy Roles

Install or update required roles with Ansible Galaxy:

### Install Roles
```bash
ansible-galaxy install -r roles/requirements.yml
```

# install docker grafana

install docker grafana

```
ansible-playbook -i hosts --user dev --extra-vars "hosts=host_name" --vault-password-file=password_file playbooks/grafana-docker-install.yml
```

# install docker jenkins

install docker jenkins

```
ansible-playbook -i hosts --user dev --extra-vars "hosts=host_name" --vault-password-file=password_file playbooks/jenkins-docker-install.yml
```
