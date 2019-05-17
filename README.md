 Ansible role: ntp
======================

[![Build Status](https://travis-ci.org/cahos-bodensee/role-ntp.svg?branch=master)](https://travis-ci.org/chaos-bodensee/role-ntp)

This role provide a compliance for install ntp on your target host.

## Requirements

This role was developed using Ansible 2.7 Backwards compatibility is not guaranteed.

Supported platforms:

```
Please have a look into the meta file for this kind of information!
```

## Role Variables

This role has multiple variables. The defaults for all these variables are the following:

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
  - 0.pool.ntp.org iburst
  - 1.pool.ntp.org iburst
  - 2.pool.ntp.org iburst
  - 3.pool.ntp.org iburst

# Enable or disable ntp statistics
# Default is false
ntp_statistics: false
```

## Dependencies

None

## Example Playbook

This is a sample playbook file for deploying the Ansible Galaxy ntp role in a localhost.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: diodonfrost.ntp
```

## Local Testing

The preferred way of locally testing the role is to use Docker. You will have to install Docker on your system.

You can also use vagrant and Virtualbox with vagrant to run tests locally. You will have to install Virtualbox and Vagrant on your system. For all our tests we use test-kitchen.

Next install test-kitchen:

```shell
# Install dependencies
gem install bundler
bundle install
```

### Testing with Docker

```shell
# List all tests with kitchen
kitchen list

# fast test on one machine
kitchen test default-centos-7

# test on all machines
kitchen test

# for development, create environment
kitchen create default-centos-7

# Apply ansible playbook
kitchen converge default-centos-7

# Apply inspec tests
kitchen verify default-centos-7
```

### Testing with Virtualbox

```shell
# Specify kitchen file on Linux
export KITCHEN_YAML=.kitchen-vagrant.yml

# fast test on one machine
kitchen test os-packaging-freebsd-112
```
### Testing Windows and Solaris with Virtualbox

Windows and Solaris can only be test with Virtualbox provider,do not use 'kitchen test' command for testing Windows and Solaris environment. There 4 steps you will be using with test-kitchen as part of your workflow.

First of all we must set the kitchen file:
```shell
# For testing Windows
export KITCHEN_YAML=.kitchen-windows.yml

# For testing Solaris
export KITCHEN_YAML=.kitchen-solaris.yml
```

Provision the virtual machines, a Linux machine to run Ansible and Windows/Solaris machines to apply playbook again:
```shell
# deploy machines
kitchen create

# Launch playbook
kitchen converge
```

Finaly launch inspec tests:
```shell
kitchen verify
```

For cleaning environment use:
```shell
kitchen destroy
```

## License

Apache 2

## Resources

[ntp on ubuntu](https://doc.ubuntu-fr.org/ntp)

## Author Information

This role was created in 2018 by diodonfrost.
