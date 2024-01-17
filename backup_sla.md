# Backup SLA Documentation

### Backup Coverage:
- **MySQL** - Agama Application Database 
- **InfluxDB** - Telegraf Log Database

### RPO (Recovery Point Objective):
- Maximum data loss allowed is 24 hours.

### Versioning and Retention:
- **Full backup** - Every Sunday @ 20:00 UTC
- **Incremental backup** - Every another day @ 20:00 UTC
- Store backups for 30 days

### Usability Checks:
- Regular checks of backup integrity and consistency.

### Restoration Criteria:
  Backup should be restored in the event of:
- Database corruption or loss.
- Unintentional data deletion.
- Critical configuration changes leading to issues.

### RTO (Recovery Time Objective):
- Aim to restore within 3 hours of identifying the issue.

### Restore Procedure
- Read backup_restore.md