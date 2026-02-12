###
Day 19 – Shell Scripting Project: Log Rotation, Backup & Crontab
🔹 Task 1: Log Rotation Script
File: log_rotate.sh
#!/bin/bash
set -euo pipefail

LOG_DIR="${1:-}"

if [ -z "$LOG_DIR" ]; then
    echo "Usage: $0 <log_directory>"
    exit 1
fi

if [ ! -d "$LOG_DIR" ]; then
    echo "Error: Directory does not exist."
    exit 1
fi

echo "Processing directory: $LOG_DIR"

# Count before compression
COMPRESS_COUNT=$(find "$LOG_DIR" -name "*.log" -mtime +7 | wc -l)

# Compress .log files older than 7 days
find "$LOG_DIR" -name "*.log" -mtime +7 -exec gzip {} \;

# Count files to delete
DELETE_COUNT=$(find "$LOG_DIR" -name "*.gz" -mtime +30 | wc -l)

# Delete .gz older than 30 days
find "$LOG_DIR" -name "*.gz" -mtime +30 -delete

echo "Compressed files: $COMPRESS_COUNT"
echo "Deleted old archives: $DELETE_COUNT"

Sample Run
./log_rotate.sh /var/log/myapp

🔹 Task 2: Server Backup Script
File: backup.sh
#!/bin/bash
set -euo pipefail

SOURCE="${1:-}"
DEST="${2:-}"

if [ -z "$SOURCE" ] || [ -z "$DEST" ]; then
    echo "Usage: $0 <source_directory> <backup_destination>"
    exit 1
fi

if [ ! -d "$SOURCE" ]; then
    echo "Error: Source directory does not exist."
    exit 1
fi

mkdir -p "$DEST"

TIMESTAMP=$(date +%Y-%m-%d)
ARCHIVE="$DEST/backup-$TIMESTAMP.tar.gz"

echo "Creating backup..."

tar -czf "$ARCHIVE" "$SOURCE"

if [ -f "$ARCHIVE" ]; then
    SIZE=$(du -h "$ARCHIVE" | cut -f1)
    echo "Backup created successfully."
    echo "Archive: $ARCHIVE"
    echo "Size: $SIZE"
else
    echo "Backup failed!"
    exit 1
fi

# Delete backups older than 14 days
find "$DEST" -name "backup-*.tar.gz" -mtime +14 -delete

echo "Old backups cleaned."

Sample Run
./backup.sh /etc /backups

🔹 Task 3: Crontab
View Current Cron Jobs
crontab -l

Cron Syntax
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of week (0-7)
│ │ │ └──── Month (1-12)
│ │ └────── Day of month (1-31)
│ └──────── Hour (0-23)
└────────── Minute (0-59)

Cron Entries
Run log_rotate.sh every day at 2 AM
0 2 * * * /path/to/log_rotate.sh /var/log/myapp

Run backup.sh every Sunday at 3 AM
0 3 * * 0 /path/to/backup.sh /etc /backups

Run health check every 5 minutes
*/5 * * * * /path/to/health_check.sh

🔹 Task 4: Scheduled Maintenance Script
File: maintenance.sh
#!/bin/bash
set -euo pipefail

LOGFILE="/var/log/maintenance.log"

log() {
    echo "$(date '+%Y-%m-%d %H:%M:%S') - $1" >> "$LOGFILE"
}

run_log_rotation() {
    log "Starting log rotation"
    /path/to/log_rotate.sh /var/log/myapp >> "$LOGFILE" 2>&1
    log "Log rotation completed"
}

run_backup() {
    log "Starting backup"
    /path/to/backup.sh /etc /backups >> "$LOGFILE" 2>&1
    log "Backup completed"
}

main() {
    log "Maintenance job started"
    run_log_rotation
    run_backup
    log "Maintenance job finished"
}

main

Cron Entry (Daily at 1 AM)
0 1 * * * /path/to/maintenance.sh

🔹 Sample maintenance.log Output
2026-02-08 01:00:01 - Maintenance job started
2026-02-08 01:00:02 - Starting log rotation
Compressed files: 5
Deleted old archives: 2
2026-02-08 01:00:10 - Log rotation completed
2026-02-08 01:00:11 - Starting backup
Backup created successfully.
Archive: /backups/backup-2026-02-08.tar.gz
Size: 12M
2026-02-08 01:00:20 - Backup completed
2026-02-08 01:00:21 - Maintenance job finished

🔹 What I Learned

Real automation combines multiple scripts.

Strict mode prevents production failures.

Cron enables scheduled DevOps operations.

Logging is critical for troubleshooting.

Always validate input and handle errors safely.

🔥 Real DevOps Relevance

Production log management

Automated server backups

Scheduled maintenance jobs

Disaster recovery preparation

Compliance & audit logging

🔹 Interview Talking Point

If asked:

How would you implement log rotation?

Answer:
Use a bash script with find and mtime to compress old logs and delete older archives, then schedule via cron with proper logging and strict mode enabled.

How do you ensure backups are valid?

Answer:
Check archive existence, validate exit codes, log output, and clean up old backups automatically.
