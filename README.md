Ansible role: Upsource
=========
[![Build Status](https://travis-ci.org/uridium/ansible-role-upsource.svg)](https://travis-ci.org/uridium/ansible-role-upsource)
[![Galaxy](https://img.shields.io/badge/galaxy-uridium.upsource-blue.svg)](https://galaxy.ansible.com/uridium/upsource)

An Ansible role that installs and configures Upsource service on Debian systems.

Requirements
------------

* openjdk-11
* unzip

`openjdk-11-jre-headless` and `unzip` packages are defined in `tasks/main.yml`.

[Upsource requirements](https://www.jetbrains.com/help/upsource/prerequisites.html)

Role Variables
--------------

Available variables are listed down below (see `defaults/main.yml`):

```yaml
upsource_version: '2019.1.1644'
upsource_download_url: 'https://download.jetbrains.com/upsource/upsource-{{ upsource_version }}.zip'

upsource_basedir: '/opt'
upsource_workdir: '{{ upsource_basedir }}/upsource'
upsource_lsb_script: '{{ upsource_workdir }}/bin/upsource.sh'

upsource_user: 'upsource'
upsource_group: 'upsource'

upsource_memlock: unlimited
upsource_nofile: 100000
upsource_nproc: 32768
upsource_as: unlimited
```

JVM options are defined in [files](files/) directory.

Dependencies
------------

None

Example Playbook
----------------

```yaml
    - hosts: upsource.host
      remote_user: admin
      become: True
      gather_facts: True

      roles:
        - role: uridium.upsource
```

License
-------

MIT
