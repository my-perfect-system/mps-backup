# `mps.backup` Ansible Collection

Per-user backup restore — SSH keys, config, brave bookmarks, home
directory. Uses `ansible.posix.synchronize` for efficient pulling.

## Galaxy metadata

- **namespace**: `mps`
- **name**: `backup`
- **version**: `0.3.1`
- **dependencies**: `mps.base`, `ansible.posix`

See [`galaxy.yml`](galaxy.yml) for the canonical values.

## Roles

| Role | Purpose |
|---|---|
| [`mps.backup.backup`](roles/backup/README.md) | Per-user SSH keys + config + authorized_keys + brave bookmarks + home directory restore. |

## Required input

Set host-group variables to point to your backup source:

```yaml
backup_ssh_source: /var/backups/alice/ssh
backup_source: /var/backups/alice/home
backup_enable_persist_brave: true
```

## Installation

```bash
ansible-galaxy collection install mps.backup
```

## Usage

```yaml
- hosts: restore_targets
  become: true
  roles:
    - mps.base.identity
    - mps.backup.backup
```

## Caveats

- Restore is **conservative** (`synchronize ... delete: false`) — existing files are not removed.
- The role assumes SSH keys live in `{{ backup_ssh_source }}/keys/`, config in `{{ backup_ssh_source }}/config/`, and authorized_keys in `{{ backup_ssh_source }}/authorized/`.

## Documentation

- [`AGENTS.md`](AGENTS.md) — developer conventions
- `roles/backup/README.md` — per-role variable docs

## License

GPL-3.0-or-later
