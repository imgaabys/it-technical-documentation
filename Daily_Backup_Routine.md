# 💾 Enterprise Daily Backup & Data Integrity Routine

This guide defines the standard procedures for daily backups, ensuring data availability, disaster recovery readiness, and compliance with retention policies.

---

## 🕒 Phase 1: The "3-2-1" Backup Strategy
*We follow the industry-standard rule for maximum safety:*
- **3** Copies of data (Primary + 2 Backups).
- **2** Different media types (e.g., Cloud + Local Disk/NAS).
- **1** Copy stored **Off-site** (Cloud or Remote Data Center).

---

## 📝 Phase 2: Daily Execution Checklist

### 1. Automated Task Verification 🤖
- [ ] **Job Status:** Check the backup console (e.g., Veeam, Synology, or Azure Backup) for "Success" status.
- [ ] **Log Review:** Inspect logs for "Warnings" or skipped files.
- [ ] **Storage Capacity:** Ensure the target repository (Cloud/Local) has at least 20% free space.

### 2. Database & Critical Apps 🗄️
- [ ] **SQL Server:** Verify Transaction Log backups (hourly) and Full backups (daily).
- [ ] **ERP/CRM:** Confirm that the application-level backup was completed before the VM snapshot.

### 3. Off-site Sync ☁️
- [ ] **Cloud Upload:** Verify that the local daily backup was successfully synced to Azure/AWS/Wasabi.
- [ ] **Immutability:** Check if the "Object Lock" (Immutable backup) is active to prevent ransomware deletion.

---

## ⚠️ Common Issues & Troubleshooting (Backup Failures)

| Symptom / Error | Root Cause | Solution (Fix) |
| :--- | :--- | :--- |
| **❌ VSS Snapshot Failed** | Volume Shadow Copy service error on the VM. | Restart the VSS service and check for disk I/O bottlenecks. |
| **❌ Connection Timeout** | Network instability during Cloud upload. | Check bandwidth logs or reschedule the sync to a lower-traffic window. |
| **❌ Insufficient Space** | Retention policy kept too many old versions. | Manually prune old recovery points or increase storage quota. |
| **❌ Partial Success** | Files locked by users during the backup window. | Ensure "Changed Block Tracking" (CBT) is enabled or use Agent-based backup. |

---

## 🛡️ Phase 3: Recovery Testing (The "Real" Backup)
> [!IMPORTANT]
> **A backup is only a backup if it can be restored.**
- [ ] **Monthly Test:** Perform a "Sandbox Restore" of a random file or VM once a month.
- [ ] **Integrity Check:** Run a "Health Check" (CheckSum) on the backup files to prevent bit rot.

---

## 📝 Admin Pro-Tip
> [!CAUTION]
> **Ransomware Alert:** Always use a dedicated service account for backups with "Write-Only" permissions to the repository. This prevents a compromised user account from deleting the backup history.

---
*Maintained by Gabriella Costa | Software Engineering Student*
