[![Ansible Galaxy](https://ansible.l3d.space/svg/l3d.ntp.svg)](https://galaxy.ansible.com/ui/standalone/roles/l3d/ntp/)
[![BSD-3 Clause](https://ansible.l3d.space/svg/l3d.ntp_license.svg)](LICENSE)
[![Maintainance](https://ansible.l3d.space/svg/l3d.ntp_maintainance.svg)](https://ansible.l3d.space/#l3d.ntp)

 Ansible role ntp
======================

Ansible role to install and configure the Network Time Protocol (NTP) Daemon.

This role was built with support for a variety of operating systems. Including Debian/Ubuntu, RHEL, Suse and Archlinux based Linux versions as well as FreeBSD, Darwin and OpenBSD.

## Role Variables

In addition to the operating system-dependent variables, there are the following default values to adjust:

```yaml
---
# defaults file for ansible-role-ntp

# Restrict acces on ntp server
# Default is: ::1, 127.0.0.1
ntp_restrict:
  - default nomodify notrap nopeer noquery
  - 127.0.0.1
  - ::1

# Ntp server to use for date synchronization
# Default is worldwide pool
ntp_servers:
  - ptbtime1.ptb.de
  - ptbtime3.ptb.de
  - 0.pool.ntp.org iburst
  - 1.pool.ntp.org iburst
  - 2.pool.ntp.org iburst
  - 3.pool.ntp.org iburst

# optionally set timezone
ntp_set_time_zone: false
ntp_timezone: 'Europe/Berlin'

# Enable or disable ntp statistics
ntp_statistics: false

# version check for this playbook (true is recomended)
submodules_versioncheck: false
```

## Example Usage

### Getting this Role
You can install this role using ansible Galaxy:
```bash
ansible-galaxy install l3d.ntp
```

Or download or clone this git repo. Example:
```bash
git clone https://github.com/roles-ansible/ansible_role_ntp.git l3d.ntp
```
### Using this role in a Playbook
```yml
---
- name: Install and Configure NTP
  hosts: example.com
  roles:
    - {role: l3d.ntp, tags: ntp}
  vars:
    submodules_versioncheck: true
    ntp_set_time_zone: true
    ntp_timezone: Zulu
    # In this example, we enabled optional version check
    # and set timezone to Zulu.
```


## Resources
[ntp on ubuntu](https://doc.ubuntu-fr.org/ntp)

## Requirements
The ``community.general`` collection is required for some parts of this ansible role.
You can install it with this command:
```bash
ansible-galaxy collection install -r requirements.yml --upgrade
```

## Author Information

+ This role was created in 2018 by diodonfrost.
+ This role was updated and maintained since 2019 by L3D *([DO1JLR](https://github.com/do1jlr))*
+ In 2023 this role moved from ``do1jlr.ntp`` to ``l3d.ntp`` Namespace.

## Contribution
Pleas feel free to open a issue or *(even better)* create a Pull Request if there is a problem or you missing a feature or something like that.
