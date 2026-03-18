# 🛡️ Enterprise User Offboarding & Security De-provisioning

This guide outlines the critical steps to securely revoke access and reclaim assets when an employee leaves the organization, ensuring data integrity and compliance.

---

## 🛑 Phase 1: Immediate Access Revocation
*These steps must be completed as soon as the HR notification is received:*
- [ ] **Account Status:** Disable the account in **Active Directory** (Do NOT delete yet).
- [ ] **Password Reset:** Force a password change to a random complex string.
- [ ] **Active Sessions:** Sign out of all **Microsoft 365** active sessions (revoke refresh tokens).
- [ ] **MFA Reset:** Remove the user's phone/method from **Multi-Factor Authentication**.

---

## 📂 Phase 2: Data & Asset Management

### 1. Exchange Online & Teams 📧
- [ ] **Convert to Shared Mailbox:** Transform the mailbox to a Shared Mailbox to save license costs.
- [ ] **Delegate Access:** Grant "Full Access" to the manager or successor.
- [ ] **Out of Office:** Set an automated reply informing that the user has left the company.

### 2. OneDrive & SharePoint ☁️
- [ ] **File Transfer:** Grant the manager access to the user's **OneDrive for Business** files.
- [ ] **Access Removal:** Remove the user from any specific SharePoint site permissions.

### 3. Physical Assets 💻
- [ ] **Equipment Recovery:** Reclaim Laptop, Mobile, Token, and Badge.
- [ ] **Asset Registry:** Update the status to "In Stock" or "Ready for Re-imaging".

---

## ⚠️ Common Issues & Troubleshooting (Security Risks)

| Symptom / Risk | Root Cause | Solution (Fix) |
| :--- | :--- | :--- |
| **❌ User still sending emails** | Mobile device cache (ActiveSync). | Wipe the corporate data from the device via **Intune** or Exchange Admin. |
| **❌ Files missing in OneDrive** | 30-day retention period expired. | Restore from the "Second-stage Recycle Bin" or backup tool. |
| **❌ License still assigned** | Manual step skipped. | Unassign M365 license after converting to Shared Mailbox to stop billing. |
| **❌ Third-party access** | SaaS apps not linked to SSO. | Manually disable accounts in external portals (e.g., Adobe, Zoom, Canva). |

---

## 📜 Phase 3: Final Audit & Retention
- [ ] **Group Removal:** Remove the user from all **Security Groups** and Distribution Lists.
- [ ] **Hide from GAL:** Hide the email address from the Global Address List (M365).
- [ ] **Calendar Cleanup:** Remove or reassign any recurring meetings owned by the user.

---

## 📝 Admin Security Note
> [!IMPORTANT]
> **Data Retention:** Follow the company's policy (usually 30 to 90 days) before permanently deleting the AD object. Always ensure a backup exists before the final deletion.

> [!CAUTION]
> If the user was an Admin, immediately audit any **Service Accounts** or **API Keys** they might have created to prevent "Backdoor" access.

---
*Maintained by Gabriella Costa | Software Engineering Student*
