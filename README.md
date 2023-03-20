# Mount CIFS volume

This roles mounts a CIFS volume on a Linux system.

## Role Variables

| Name            | Default value  | Description                                  | Example                                           |
| --------------- | -------------- | -------------------------------------------- | ------------------------------------------------- |
| `cifs_volume`   | `None`         | The CIFS volume to mount.                    | `//cdh1arch.epfl.ch/project_replica`              |
| `mount_point`   | `mnt/cifs`     | The mount point.                             | `/mnt/project_replica`                            |
| `creds_uuid`    | Generated UUID | id of the file containg the credentials used | `cifs_creds`                                      |
| `fstab_options` | `defaults`     | The options to use in the fstab entry.       | `defaults,vers=3.0,credentials=/etc/cifs_creds`   |
| `username`      | `username`     | The username to use for the mount.           | `{{ lookup('ansible.builtin.env', 'USER') }}`     |
| `password`      | `password`     | The password to use for the mount.           | `{{ lookup('ansible.builtin.env', 'PASSWORD') }}` |
| `domain`        | `domain`       | The domain to use for the mount.             | `domain`                                          |

## Example Playbook

```yml
    - hosts: servers
      roles:
         - role: ansible_mount_cifs_volume
           vars:
            cifs_volume: "//server/share"
            ...
```

## License

GNU GENERAL PUBLIC LICENSE Version 3

## Author Information

Emmanuel Jaep: :octocat: [jaepetto](https://github.com/jaepetto)
