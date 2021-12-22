Role Name
=========

This Ansible role installs and configures `syncthing` Debian-based (as of now, Ubuntu and Debian) distros.

Requirements
------------

- `community.general` from Ansible Galaxy
- `systemd`

Role Variables
--------------

| variable              | explanation                                                                        | default                   |
| --------------------- | ---------------------------------------------------------------------------------- | ------------------------- |
| `channel`             | Release channel for `syncthing`. Possible values: `candidate`, `stable`            | `stable`                  |
| `syncthing_user`      | User to run `syncthing` with                                                       | `syncthing`               |
| `syncthing_group`     | Group name of `syncthing_user`                                                     | `syncthing`               |
| `syncthing_home`      | Home folder of `syncthing_user`. Used to store configurations in `XDG_CONFIG_DIRS` | `/var/lib/syncthing`      |
| `sync_dir`            | Default sync directory                                                             | `/var/lib/syncthing/data` |
| `ansible_user_access` | Whether `ansible_user` can access the sync directory                               | `yes`                     |
| `gui_address`         | Address and port number of `syncthing`'s Web GUI                                   | `127.0.0.1:8384`          |

Dependencies
------------

- `community.general` collection

Example Playbook
----------------

Installing `syncthing` on hosts `servers`, with `stable` channel release of `syncthing`, and setting the default sync folder to `/mnt/data/syncthing`. **`become : yes` is necessary if `ansible_user` is not `root`.**

```yaml
- hosts: servers
  roles:
    - { role: zoenglinghou.syncthing, channel: stable, sync_dir: /mnt/data/syncthing, become: yes }
```

License
-------

GPL-3.0-only
