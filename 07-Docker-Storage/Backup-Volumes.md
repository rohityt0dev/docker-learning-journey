# Docker Volume Backup and Restore

## Objective
Learn how to back up and restore Docker volume data.

## 1. What Is a Docker Volume Backup?

A volume backup creates an archive of data stored in a Docker volume. It helps protect important data and restore it when needed.

## 2. Create a Docker Volume

```bash
docker volume create my-data
```

Add sample data:

```bash
docker run --rm \
  -v my-data:/data \
  alpine sh -c "echo 'Hello Docker Backup' > /data/backup.txt"
```

## 3. Back Up a Volume

Create a backup directory on the host:

```bash
mkdir -p backups
```

Back up the volume to a compressed archive:

```bash
docker run --rm \
  -v my-data:/data:ro \
  -v "$(pwd)/backups:/backup" \
  alpine \
  tar -czf /backup/my-data-backup.tar.gz -C /data .
```

The backup is saved to `backups/my-data-backup.tar.gz`.

## 4. Verify the Backup

```bash
ls -lh backups/
```

List the archive contents:

```bash
tar -tzf backups/my-data-backup.tar.gz
```

## 5. Restore a Volume

Create a new volume:

```bash
docker volume create my-data-restored
```

Restore the archive into it:

```bash
docker run --rm \
  -v my-data-restored:/data \
  -v "$(pwd)/backups:/backup:ro" \
  alpine \
  tar -xzf /backup/my-data-backup.tar.gz -C /data
```

## 6. Verify Restored Data

```bash
docker run --rm \
  -v my-data-restored:/data:ro \
  alpine cat /data/backup.txt
```

Expected output:

```text
Hello Docker Backup
```

## 7. Best Practices

- Back up important volumes regularly.
- Store backups outside the Docker host when possible.
- Test restores to verify that backups work.
- Protect backup files because they may contain sensitive data.
- For databases, use database-aware backup procedures to ensure consistency.

## Summary

Docker volumes can be backed up by archiving their contents and restored into another volume.

**Workflow:** Create Volume → Back Up → Verify → Restore → Test