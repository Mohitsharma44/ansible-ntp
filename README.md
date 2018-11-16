Role Name
=========
[![Build Status](https://travis-ci.org/Mohitsharma44/ansible-ntp.svg?branch=master)](https://travis-ci.org/Mohitsharma44/ansible-ntp)

configure and run ntp client on Ubuntu

Requirements
------------

Tested with Ubuntu 14.04 and 16.04 only

Role Variables
--------------

``` yaml
# defaults file for ansible-ntp

ntp_enabled: true
ntp_timezone: "America/New_York"
ntp_manage_config: false

ntp_packages:
  - ntp
  - tzdata

ntp_driftfile: /var/lib/ntp/drift

# NTP server area configuration (leave empty for 'Worldwide').
# See: http://support.ntp.org/bin/view/Servers/NTPPoolServers

ntp_area: ''
ntp_servers:
  - "0{{ '.' + ntp_area if ntp_area else '' }}.pool.ntp.org iburst"
  - "1{{ '.' + ntp_area if ntp_area else '' }}.pool.ntp.org iburst"
  - "2{{ '.' + ntp_area if ntp_area else '' }}.pool.ntp.org iburst"
  - "3{{ '.' + ntp_area if ntp_area else '' }}.pool.ntp.org iburst"

ntp_restrict:
  - "127.0.0.1"
  - "::1"
```

Example Playbook
----------------

``` yaml
- hosts: all
  gather_facts: no

  tasks:
  - include_role:
    name: mohitsharma44.ansible_ntp
```

License
-------

MIT

Author Information
------------------

Mohit Sharma (Mohitsharma44@gmail.com)
