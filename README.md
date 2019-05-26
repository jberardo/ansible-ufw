# UFW Ansible Role

Install and configure UFW on Linux.

## Requirements

None.

## Variables

See `defaults/main.yml`.

ufw_dependencies: Required apt packages

`ufw_default_incoming_policy`: Allow or deny incoming packets

`ufw_default_outgoing_policy`: Allow or deny outgoing packets

`ufw_logging`: Enable or disable logging

`ufw_rules`: List of ufw rules (see example below)

## Example

```yml
- hosts: host1
  become: yes
  vars_files:
    - vars/main.yml
  roles:
    - ufw
```

Variables example:

```yml
ufw_default_incoming_policy: deny
ufw_default_outgoing_policy: allow

ufw_logging: 'off'

ufw_rules:
  - rule: allow
    interface: "{{ ansible_default_ipv4['interface'] }}"
    to_port: 22
    protocol: tcp
```