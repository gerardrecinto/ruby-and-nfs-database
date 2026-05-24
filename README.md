# Ruby NFS & Database Automation

Ruby scripts for automating NFS mount lifecycle and database backup/restore operations. Originally written to manage shared storage and database tasks across a small lab cluster.

![Ruby](https://img.shields.io/badge/Ruby-3.x-CC342D?logo=ruby&logoColor=white)
![Shell](https://img.shields.io/badge/Shell-Bash-4EAA25?logo=gnubash&logoColor=white)
![License: MIT](https://img.shields.io/badge/License-MIT-22c55e)

---

## Scripts

| Script | Purpose |
|---|---|
| `nfs_mount.rb` | Mount NFS shares, verify connectivity, retry on failure |
| `nfs_unmount.rb` | Graceful unmount with active-connection check |
| `db_backup.rb` | Dump database to timestamped archive with retention cleanup |
| `db_restore.rb` | Restore from a specific backup file or latest snapshot |

---

## Usage

```bash
gem install bundler
bundle install

# Mount an NFS share
ruby nfs_mount.rb --host nfs-server.local --share /exports/data --mount /mnt/data

# Back up a database
ruby db_backup.rb --host db-host --database mydb --output /backups/ --keep 7

# Restore latest snapshot
ruby db_restore.rb --host db-host --database mydb --backup /backups/mydb_latest.sql.gz
```

---

## Requirements

- Ruby 3.x
- NFS client tools (`mount.nfs` / `nfsmount`)
- `pg_dump` / `mysqldump` on the PATH for database targets
