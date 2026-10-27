# Docker Volume Restore

## Objective

Learn how to restore Docker volume data from a compressed backup archive.

## 1. What Is Volume Restoration?

Volume restoration is the process of recovering data from a backup archive into a Docker volume.

It is useful when recovering lost data, migrating applications, or recreating containers.

## 2. Create a Backup Directory

Make sure your backup archive is available on the host:

```bash
mkdir -p backups
ls -lh backups/
```

Example backup file:

```text
backups/
└── my-data-backup.tar.gz
```

## 3. Create a New Docker Volume

```bash
docker volume create my-data-restored
```

Verify the volume:

```bash
docker volume ls
```

## 4. Restore the Backup

Run the following command from the directory containing `backups/`:

```bash
docker run --rm \
  -v my-data-restored:/data \
  -v "$(pwd)/backups:/backup:ro" \
  alpine \
  tar -xzf /backup/my-data-backup.tar.gz -C /data
```

### Command Explanation

- `--rm` — Removes the temporary container after it exits.
- `my-data-restored:/data` — Mounts the destination volume.
- `backups:/backup:ro` — Makes the backup directory available as read-only.
- `tar -xzf` — Extracts the compressed archive.
- `-C /data` — Extracts the files into the volume.

**Important:** This example assumes the archive was created with `tar -czf ... -C /data .`, as shown in `Backup-Volumes.md`.

## 5. Verify the Restored Data

List the restored files:

```bash
docker run --rm \
  -v my-data-restored:/data:ro \
  alpine \
  ls -la /data
```

Read a sample file:

```bash
docker run --rm \
  -v my-data-restored:/data:ro \
  alpine \
  cat /data/backup.txt
```

Expected output, if the file contains the sample data from the backup exercise:

```text
Hello Docker Backup
```

## 6. Use the Restored Volume

You can mount the restored volume into another container:

```bash
docker run -d \
  --name my-nginx \
  -p 8080:80 \
  -v my-data-restored:/usr/share/nginx/html \
  nginx
```

Ensure the restored volume contains the files your application expects.

## 7. Clean Up

Remove the test container:

```bash
docker rm -f my-nginx
```

Remove the restored volume only if you no longer need its data:

```bash
docker volume rm my-data-restored
```

**Warning:** Removing a volume permanently deletes its stored data. Verify your backup before deleting the original volume.

## Best Practices

- Verify that the backup archive exists before restoring.
- Restore into a new volume when possible.
- Check file permissions and ownership after restoration.
- Test restored data before using it in production.
- Use database-aware backup and recovery procedures for databases.
- Keep backup copies on separate storage.

## Summary

Docker volume restoration recovers data from an archive into a Docker volume.

**Workflow:** Locate Backup → Create Volume → Restore → Verify → Use