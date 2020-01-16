 Ansible role: ntp
======================

[![Build Status](https://travis-ci.org/chaos-bodensee/role-ntp.svg?branch=master)](https://travis-ci.org/chaos-bodensee/role-ntp)

This role provide a compliance for install ntp on your target host.

## Requirements

This role was developed using Ansible 2.7 Backwards compatibility is not guaranteed.

```
Please have a look into the meta file for supportet platform overview!

Please note: It could need some fixes on exotic untested devices!
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

## Resources

[ntp on ubuntu](https://doc.ubuntu-fr.org/ntp)

## Author Information

This role was created in 2018 by diodonfrost.
This role was updated in 2019 and 2020 by L3D *([DO1JLR](https://github.com/do1jlr))*
