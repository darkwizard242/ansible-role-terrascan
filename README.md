[![build-test](https://github.com/darkwizard242/ansible-role-terrascan/workflows/build-and-test/badge.svg?branch=master)](https://github.com/darkwizard242/ansible-role-terrascan/actions?query=workflow%3Abuild-and-test) [![release](https://github.com/darkwizard242/ansible-role-terrascan/workflows/release/badge.svg)](https://github.com/darkwizard242/ansible-role-terrascan/actions?query=workflow%3Arelease) ![Ansible Role](https://img.shields.io/ansible/role/d/darkwizard242/terrascan) [![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-terrascan&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=ansible-role-terrascan) [![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-terrascan&metric=reliability_rating)](https://sonarcloud.io/dashboard?id=ansible-role-terrascan) [![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-terrascan&metric=security_rating)](https://sonarcloud.io/dashboard?id=ansible-role-terrascan) ![GitHub tag (latest SemVer)](https://img.shields.io/github/tag/darkwizard242/ansible-role-terrascan?label=release) ![GitHub repo size](https://img.shields.io/github/repo-size/darkwizard242/ansible-role-terrascan?color=orange&style=flat-square)

# Ansible Role: terrascan

Role to install (_by default_) [terrascan](https://runterrascan.io/) on **Debian/Ubuntu** and **EL** systems. **terrascan** detects compliance and security violations across Infrastructure as Code to mitigate risk before provisioning cloud native infrastructure.

## Requirements

None.

## Role Variables

Available variables are listed below (located in `defaults/main.yml`):

### Variables list:

```yaml
terrascan_app: terrascan
terrascan_version: 1.19.1
terrascan_os: "{{ ansible_system }}"
terrascan_architecture_map:
  amd64: x86_64
  arm: arm64
  x86_64: x86_64
  armv6l: armv6
  armv7l: armv7
  aarch64: arm64
  32-bit: "i386"
  64-bit: x86_64
terrascan_dl_url: https://github.com/tenable/{{ terrascan_app }}/releases/download/v{{ terrascan_version }}/{{ terrascan_app }}_{{ terrascan_version }}_{{ terrascan_os }}_{{ terrascan_architecture_map[ansible_architecture] }}.tar.gz
terrascan_bin_path: /usr/local/bin
terrascan_file_owner: root
terrascan_file_group: root
terrascan_file_permission_mode: '0755'
```

### Variables table:

Variable                       | Description
------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------
terrascan_app                  | Defines the app to install i.e. **terrascan**
terrascan_version              | Defined to dynamically fetch the desired version to install. Defaults to: **1.19.1**
terrascan_os                   | Defines os type.
terrascan_architecture_map     | Defines os architecture.
terrascan_dl_url               | Defines URL to download the terrascan binary from.
terrascan_bin_path             | Defined to dynamically set the appropriate path to store terrascan binary into. Defaults to (as generally available on any user's PATH): **/usr/local/bin**
terrascan_file_owner           | Owner for the binary file of terrascan.
terrascan_file_group           | Group for the binary file of terrascan.
terrascan_file_permission_mode | Defines the permission mode level for the file. Defaults to: `0755`

## Dependencies

None

## Example Playbook

For default behaviour of role (i.e. installation of **terrascan**) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.terrascan
```

For customizing behavior of role (i.e. specifying the desired **terrascan** version) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.terrascan
  vars:
    terrascan_version: 1.15.0
```

For customizing behavior of role (i.e. placing binary of **terrascan** package in different location) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.terrascan
  vars:
    terrascan_bin_path: /bin/
```

## License

[MIT](https://github.com/darkwizard242/ansible-role-terrascan/blob/master/LICENSE)

## Author Information

This role was created by [Ali Muhammad](https://www.alimuhammad.dev/).
