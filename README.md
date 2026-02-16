# New Relic Infrastructure Agent (RHEL)

This playbook installs and configures the **New Relic Infrastructure Agent** on RHEL hosts in **privileged mode**.

---

## Requirements

- RHEL hosts with SSH access
- Sudo privileges
- New Relic license key
- Ansible / AAP setup

---

## Playbook Tasks

1. Create `/etc/newrelic-infra.yml` with license key
2. Add New Relic repository
3. Refresh only newrelic-infra repository cache
4. Install `libcap` (for privileged mode)
5. Install and start `newrelic-infra` service
6. Restart service after installation

---

## Using in AAP

1. **Inventory:** create from file or manually  
2. **Credential:** SSH username/password + sudo  
3. **Survey:** add `newrelic_license_key` to input license key  

Launch the job template to install the agent on selected hosts.

---

## Variables
### survey variable (required) :
- `newrelic_license_key` – New Relic license key 
### hosts variables : (in hosts.ini or create manuaaly in AAP)
- `ansible_host` – ip address of the host
- `ansible_user` – username of the host user 
- `rhel_arch` – `x86_64` or `aarch64`  
- `debian_version` – RHEL vesrsion (`7`, `8`, `9`,  `10`)  

