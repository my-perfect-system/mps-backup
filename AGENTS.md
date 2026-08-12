# AGENTS.md — mps-backup

Per-user backup restore — SSH keys (private + config + authorized_keys),
brave bookmarks, home directory. Uses `ansible.posix.synchronize` for
efficient pulling.

## Galaxy

- **namespace**: `mps`
- **name**: `backup`
- **version**: `0.3.1`
- **dependencies**: `mps.base >=0.1.0`, `ansible.posix >=1.0.0`

## Roles

| Role | Description | Complexity |
|---|---|---|
| `mps.backup.backup` | Per-user restore loop (iterates `identity_users_present`). Creates `~/.ssh/`, restores SSH private keys / config / authorized_keys from `backup_ssh_source`, fixes directory permissions to 0700 (recurse), restores Brave bookmarks gated by `backup_enable_persist_brave`, restores home directory from `backup_source`. | 2 |

## Conventions

- All tasks are per-user loops with `become_user:` to switch to each user.
- `synchronize` with `delete: false` — restore is conservative; existing files are not removed.
- The role's main.yml is a single file (no install/configure sub-step split) — the original configure.yml was inlined in the refactor pass.
- Source paths are templated via `backup_ssh_source`, `backup_source`, `backup_enable_persist_brave` — these are host-group vars, declared in `examples/inventories/home/group_vars/all/mps_backup.yml`.
