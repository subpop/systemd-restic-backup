NAME
====

restic-backup.conf - Configuration file for **restic-backup**

SYNOPSIS
========

The **restic-backup.conf** file defines variables that configure **restic-backup.service** and **restic-prune.service**.

DESCRIPTION
===========

**restic** looks to environment files to determine how and where to backup. This configuration file is loaded into the service environment, allowing each variable defined in this file to be available to **restic** at runtime. In addition to the variables required by **restic** such as *RESTIC_REPOSITORY* and *RESTIC_PASSWORD*, the following variables are interpreted by **restic-backup** and **restic-prune**.

BACKUP_PATHS
: Space-separated paths to include in the backup snapshot.

BACKUP_FLAGS
: Additional arguments that are passed to **restic** when running the *backup* command.

RETENTION_DAYS
: Number daily snapshots to retain

RETENTION_WEEKS
: Number of weekly snapshots to retain

RETENTION_MONTHS
: Number of monthly snapshots to retain

RETENTION_YEARS
: Number of yearly snapshots to retain

EXAMPLE
=======

```
BACKUP_PATHS="/home/rupert /etc"
BACKUP_FLAGS="--exclude-if-present .exclude_from_backup --exclude-file /home/rupert/.restic_excludes"

RETENTION_DAYS=7
RETENTION_WEEKS=4
RETENTION_MONTHS=6
RETENTION_YEARS=3

B2_ACCOUNT_ID=XXXXXXXXXXXXXXXXXXXXXX
B2_ACCOUNT_KEY=XXXXXXXXXXXXXXXXX
RESTIC_REPOSITORY=b2:xxxxxxxxxx:/backup
RESTIC_PASSWORD=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```

SEE ALSO
========

restic(1)