# nodejs_local_install

This is an Ansible role for x64 Linux that installs NodeJS directly from
[nodejs.org](https://nodejs.org) into `~/.local` then adds it to the `PATH`
for a **single user**. It does not install NodeJS system-wide, and it is
intended for users who cannot sudo to root.

## Requirements

- (Optiona) sudo - needed when the operator is using the role to install
  NodeJS for another user.

- (Optional) A non-root user for whom NodeJS may be installed (see the
  `target_user` var below).

  If no `target_user` is provided then NodeJS is installed for the Ansible
  default user.

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
  already exist. Use this when running the role as a systems admin who is
  installing NodeJS for another user, aka the "`target_user`". Be sure to use
  the `become` directive in this case so that user directories can be created.

## Dependencies

The managed system must already have the following packages installed:

 - curl
 - jq
 - xz-utils

## Example Playbook

```yaml
- name: Install NodeJS
  hosts: localhost
  connection: local
  gather_facts: false
  vars:
    target_user: jdoe # Optional, defaults to Ansible user
    node_version: v21
  roles:
    - role: nodejs_local_install
      tags:
        - node
        - nodejs
        - devkit
      become: true   # (Optional) Needed when the operator is installing 
                     # for user 'jdoe'
```

## License

BSD

## Author Information

V01dDweller

[modeline]: # ( vim: set nu relativenumber textwidth=78 colorcolumn=80: )
