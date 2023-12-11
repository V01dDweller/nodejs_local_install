# nodejs_local_install

This is an Ansible role for x64 Linux that installs NodeJS into `~/.local`
then adds it to your `PATH`.

## Requirements

- Ansible user must be able to sudo to root. This is needed to install missing
  packages and target a non-root user if specified.
- (optional) A non-root user for whom NodeJS may be installed.

## Role Variables

- `node_version` - Defaults to `v18` (NodeJS v18) via `defaults/main.yml`
- `release_url` - Where to download NodeJS tar files. Defaults to
  https://nodejs.org/download/release
- `target_user` - (Optional) A non-root user for whom to install. User should
  already exist.

## Dependencies

None.

## Example Playbook

```yaml
- name: Install NodeJS
  hosts: localhost
  connection: local
  gather_facts: false
  vars:
    target_user: jdoe # Optional, defaults to Ansible user
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
