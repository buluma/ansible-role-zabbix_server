# [Ansible role zabbix_server](#ansible-role-zabbix_server)

Install and configure zabbix_server on your system.

|GitHub|Issues|Pull Requests|Version|Downloads|
|------|------|-------------|-------|---------|
|[![github](https://github.com/buluma/ansible-role-zabbix_server/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-zabbix_server/actions/workflows/molecule.yml)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-zabbix_server.svg)](https://github.com/buluma/ansible-role-zabbix_server/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-zabbix_server.svg)](https://github.com/buluma/ansible-role-zabbix_server/pulls/)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-zabbix_server.svg)](https://github.com/buluma/ansible-role-zabbix_server/releases/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/zabbix_server)](https://galaxy.ansible.com/ui/standalone/roles/buluma/zabbix_server/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-zabbix_server/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- become: true
  gather_facts: true
  hosts: all
  name: Converge
  roles:
    - role: buluma.zabbix_server
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-zabbix_server/blob/master/molecule/default/prepare.yml):

```yaml
---
- become: true
  gather_facts: false
  hosts: all
  name: Prepare
  roles:
    - role: buluma.bootstrap
    - role: buluma.selinux
    - role: buluma.container_docs
    - mysql_databases:
        - collation: utf8_bin
          encoding: utf8
          name: zabbix
      mysql_users:
        - name: zabbix
          password: zabbix
          priv: zabbix.*:ALL
      role: buluma.mysql
    - role: buluma.ca_certificates
    - role: buluma.zabbix_repository
    - role: buluma.core_dependencies
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-zabbix_server/blob/master/defaults/main.yml):

```yaml
---
zabbix_server_database_host: localhost
zabbix_server_database_name: zabbix
zabbix_server_database_password: zabbix
zabbix_server_database_user: zabbix
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-zabbix_server/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub |
|-------------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|
|[buluma.ca_certificates](https://galaxy.ansible.com/buluma/ca_certificates)|[![Build Status GitHub](https://github.com/buluma/ansible-role-ca_certificates/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-ca_certificates/actions)|
|[buluma.core_dependencies](https://galaxy.ansible.com/buluma/core_dependencies)|[![Build Status GitHub](https://github.com/buluma/ansible-role-core_dependencies/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-core_dependencies/actions)|
|[buluma.container_docs](https://galaxy.ansible.com/buluma/container_docs)|[![Build Status GitHub](https://github.com/buluma/ansible-role-container_docs/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-container_docs/actions)|
|[buluma.mysql](https://galaxy.ansible.com/buluma/mysql)|[![Build Status GitHub](https://github.com/buluma/ansible-role-mysql/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-mysql/actions)|
|[buluma.selinux](https://galaxy.ansible.com/buluma/selinux)|[![Build Status GitHub](https://github.com/buluma/ansible-role-selinux/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-selinux/actions)|
|[buluma.zabbix_repository](https://galaxy.ansible.com/buluma/zabbix_repository)|[![Build Status GitHub](https://github.com/buluma/ansible-role-zabbix_repository/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-zabbix_repository/actions)|

## [Context](#context)

This role is part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-zabbix_server/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/robertdebock):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/r/robertdebock/enterpriselinux)|all|
|[Debian](https://hub.docker.com/r/robertdebock/debian)|all|
|[Ubuntu](https://hub.docker.com/r/robertdebock/ubuntu)|all|

The minimum version of Ansible required is 2.12, tests have been done on:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them on [GitHub](https://github.com/buluma/ansible-role-zabbix_server/issues).

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-zabbix_server/blob/master/LICENSE).

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)

