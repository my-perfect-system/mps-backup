---
# Reference doc — auto-generated, do not edit by hand.
# Regenerate via: python3 manage/gen_role_readmes.py
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
- **License**: G, P, L, -, 3, ., 0, -, o, r, -, l, a, t, e, r
- **Platforms**: Debian (trixie)
- **Tasks file lines**: 95
