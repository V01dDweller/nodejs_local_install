# nodejs_local_install

This is an Ansible role for x64 Linux that installs NodeJS directly from
[nodejs.org](https://nodejs.org) into `~/.local` then adds it to the `PATH`
for a **single user**. It does not install NodeJS system-wide, and it is
intended for users who cannot sudo to root.

## Requirements

- Ansible user must be able to sudo to root. This is needed to install missing
  packages and target a non-root user if specified.
- (optional) A non-root user for whom NodeJS may be installed.

## Role Variables

- `node_version` - Acceptable values:

   - `v16`
   - `v18` (default via `defaults/main.yml`)
   - `v20`
   - `v21`

  **Note:** Do not use the full semantic version, use the `v` + `Major
  release` (e.g. `v21`) and allow the role to determine that latest point
  release.
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
