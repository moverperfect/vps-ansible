# VPS Ansible

This repository contains Ansible playbooks for setting up moverperfect's VPS.

## Requirements

- Ansible
- Python 3
- Ansible inventory file

## Usage

1. Clone the repository
2. Edit the host_vars/server1.yml file to include the following variables:
```yaml
ansible_become: yes 
ansible_become_method: sudo
ansible_become_pass: ""
ansible_host: 0.0.0.0
ansible_user: 
haproxy_username: 
haproxy_password:
radarr_host:
sonarr_host:
deluge_host:
```
3. Run the playbook

```bash
ansible-playbook -i inventory site.yml
```

## Cloudflared

Currently, the cloudflared service is not installed using Ansible.
To install cloudflared, run the following command:

```bash
curl -L --output cloudflared.deb https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb && 

sudo dpkg -i cloudflared.deb && 

# Only run this command if setting up a new cloudflared service
sudo cloudflared service install << TOKEN >>
```
