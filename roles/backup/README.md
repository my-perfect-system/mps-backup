---
namespace: mps
collection: backup
role: backup
---

# `mps.backup.backup`

Restore per-user backups (SSH, config, home directory)

## Default variables

| Variable | Default | Description |
|---|---|---|
| `backup_enable_persist_brave` | `false` | Restore Brave browser bookmarks from backup_source/brave/Bookmarks |
| `backup_source` | `` | Controller-side path to the backup root (contains home/ and brave/ dirs) |
| `backup_ssh_source` | `` | Controller-side path to SSH backup data (keys/, config/, authorized/ dirs) |

## Dependencies

- `mps.base.identity`

## Example usage

```yaml
- hosts: all
  roles:
    - mps.backup.backup
```

## Role metadata

- **Min Ansible version**: `2.16.0`
- **License**: GPL-3.0-or-later
- **Platforms**: Debian (trixie)
- **Tasks file lines**: 95

## Related files

- [`meta/main.yml`](meta/main.yml) — galaxy_info + role dependencies
- [`meta/argument_specs.yml`](meta/argument_specs.yml) — variable spec (the source of the variable table above)
- [`defaults/main.yml`](defaults/main.yml) — variable defaults (the source of the default values above)
