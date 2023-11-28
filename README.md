# nodejs_local_install

This is an Ansible role for x64 Linux that installs NodeJS into `~/.local`
then adds it to your `PATH`.

## Requirements

Ansible user must be able to sudo to root. This is needed to install missing
packages.

## Role Variables

- `node_version` - Defaults to `v18` (NodeJS v18) via `defaults/main.yml`
- `release_url` - Where to download NodeJS tar files. Defaults to
  https://nodejs.org/download/release

## Dependencies

None.

## Example Playbook

```yaml
- name: Install NodeJS
  hosts: localhost
  connection: local
  gather_facts: false
  roles:
    - role: nodejs_local_install
      tags:
        - node
        - nodejs
        - devkit
```

## License

BSD

## Author Information

V01dDweller

[modeline]: # ( vim: set nu relativenumber textwidth=78 colorcolumn=80: )
