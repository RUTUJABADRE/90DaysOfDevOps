## Task 1: Log Rotation Script

```bash
#!/bin/bash

LOG_DIR="$1"

# Check if argument is provided
if [ -z "$LOG_DIR" ]; then
    echo "Error: No directory provided."
    echo "Usage: $0 /path/to/log_directory"
    exit 1
fi

# Check if directory exists
if [ ! -d "$LOG_DIR" ]; then
    echo "Error: Directory '$LOG_DIR' does not exist."
    exit 1
fi

compressed=0
deleted=0

#Compresses .log files older than 7 days using gzip

files=$(find "$LOG_DIR" -name "*.log" -mtime +7)

for file in $files
do
    gzip "$file"
    ((compressed++))
done

#Deletes .gz files older than 30 days

files=$(find "$LOG_DIR" -name "*.gz" -mtime +30)

for file in $files
do
    rm "$file"
    ((deleted++))
done

echo "Compressed files: $compressed"
echo "Deleted files: $deleted"

```
![alt text](./images/task-1.png)
---
## Task 2: 

```bash
#!/bin/bash

SRC_DIR="$1"
DEST_DIR="$2"

# Check arguments
if [ -z "$SRC_DIR" ] || [ -z "$DEST_DIR" ]; then
    echo "Usage: $0 <source_directory> <backup_directory>"
    exit 1
fi

# Check source exists
if [ ! -d "$SRC_DIR" ]; then
    echo "Error: Source directory does not exist"
    exit 1
fi

# Ensure destination exists
mkdir -p "$DEST_DIR"

# Timestamp
DATE=$(date +%F)

# Archive name + path
ARCHIVE_NAME="backup-$DATE.tar.gz"
ARCHIVE_PATH="$DEST_DIR/$ARCHIVE_NAME"

# Create archive
tar -czf "$ARCHIVE_PATH" -C "$SRC_DIR" .

# Verify archive
if [ $? -ne 0 ] || [ ! -f "$ARCHIVE_PATH" ]; then
    echo "Backup failed!"
    exit 1
fi

echo "Backup successful: $ARCHIVE_NAME"

# Get size
SIZE=$(du -h "$ARCHIVE_PATH" | awk '{print $1}')
echo "Size: $SIZE"

# Delete old backups
find "$DEST_DIR" -name "backup-*.tar.gz" -mtime +14 -exec rm {} \;

echo "Old backups deleted"
```
![alt text](./images/task-2.png)

## Task 3: Crontab

```bash
# Run log_rotate.sh every day at 2 AM
0 2 * * * /home/shell-scripting/log_rotate.sh /home/shell-scripting/logfile

# Run backup.sh every Sunday at 3 AM
0 3 * * 0 /home/shell-scripting/backup.sh /home/shell-scripting/logfile /home/shell-scripting/backup

# Run health check script every 5 minutes
*/5 * * * * /home/shell-scripting/health_check.sh
```

## Task 4: Combine — Scheduled Maintenance Script

```bash
#!/bin/bash

LOG_FILE="/var/log/maintenance.log"

LOG_DIR="/home/shell-scripting/logfile"
BACKUP_DIR="/home/shell-scripting/backup"

# Function to add timestamp
log() {
    echo "$(date '+%Y-%m-%d %H:%M:%S') - $1"
}

# Redirect all output to log file
exec >> "$LOG_FILE" 2>&1

log "===== Maintenance started ====="

# 1. Call log rotation
log "Running log rotation..."
/home/shell-scripting/log_rotate.sh "$LOG_DIR"

# 2. Call backup
log "Running backup..."
/home/shell-scripting/backup.sh "$LOG_DIR" "$BACKUP_DIR"

log "===== Maintenance completed ====="
echo ""
```
crontab entry

```bash
0 1 * * * /home/shell-scripting/maintenance.sh
```
