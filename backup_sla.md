# Backup SLA Documentation

## Database Servers

### MySQL Database

**Backup Coverage:**
- Backed up: Database schemas, tables, and configuration files.
- Not backed up: Temporary files, cache, and non-essential logs.

**RPO (Recovery Point Objective):**
- Maximum data loss allowed is 1 hour.

**Versioning and Retention:**
- Retain 7 daily backup versions.
- Retain 4 weekly backup versions.
- Retain 3 monthly backup versions.
- Older backups are automatically purged.

**Usability Checks:**
- Regular automated checks of backup integrity and consistency.
- Periodic test restores to a non-production environment.

**Restoration Criteria:**
- Backup should be restored in the event of:
- Database corruption or loss.
- Unintentional data deletion.
- Critical configuration changes leading to issues.

**RTO (Recovery Time Objective):**
- Aim to restore within 2 hours of identifying the issue.

### InfluxDB

**Backup Coverage:**
- Backed up: Time-series data, configurations, and retention policies.
- Not backed up: Cached data and non-essential logs.

**RPO (Recovery Point Objective):**
- Maximum data loss allowed is 30 minutes.

**Versioning and Retention:**
- Retain 5 daily backup versions.
- Retain 2 weekly backup versions.
- Older backups are automatically purged.

**Usability Checks:**
- Regular automated checks of backup integrity and consistency.
- Periodic test restores to a non-production environment.

**Restoration Criteria:**
- Backup should be restored in the event of:
- Data corruption or loss.
- Unintentional data deletion.
- Critical configuration changes leading to issues.

**RTO (Recovery Time Objective):**
- Aim to restore within 1 hour of identifying the issue.

## Ansible Repository

**Backup Coverage:**
- Backed up: Playbooks, roles, inventories, and configuration files.
- Not backed up: Temporary files, cache, and non-essential logs.

**RPO (Recovery Point Objective):**
- Maximum data loss allowed is 4 hours.

**Versioning and Retention:**
- Retain 10 daily backup versions.
- Retain 3 weekly backup versions.
- Retain 2 monthly backup versions.
- Older backups are automatically purged.

**Usability Checks:**
- Regular automated checks of backup integrity and consistency.
- Periodic test restores to a non-production environment.

**Restoration Criteria:**
- Backup should be restored in the event of:
- Accidental deletion of important playbooks or roles.
- Loss of entire repository due to hardware failure or other catastrophic events.

**RTO (Recovery Time Objective):**
- Aim to restore within 3 hours of identifying the issue.
