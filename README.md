[![Ansible Galaxy](https://raw.githubusercontent.com/roles-ansible/ansible_role_ntp/main/.github/galaxy.svg?sanitize=true)](https://galaxy.ansible.com/do1jlr/ntp) [![MIT License](https://raw.githubusercontent.com/roles-ansible/ansible_role_ntp/main/.github/license.svg?sanitize=true)](https://github.com/roles-ansible/ansible_role_ntp/blob/main/LICENSE)

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

## Resources

[ntp on ubuntu](https://doc.ubuntu-fr.org/ntp)

## Author Information

This role was created in 2018 by diodonfrost.
This role was updated and maintained since 2019 by L3D *([DO1JLR](https://github.com/do1jlr))*

## Contribution
Pleas feel free to open a issue or *(even better)* create a Pull Request if there is a problem or you missing a feature or something like that.
