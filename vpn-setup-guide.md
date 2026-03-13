# Corporate VPN Setup & Troubleshooting Guide 🌐

This guide provides a step-by-step procedure for configuring and troubleshooting Corporate VPN connections for remote users.

## 📋 Prerequisites
* Active corporate credentials (AD Account).
* VPN Client installed (e.g., AnyConnect, FortiClient, or Windows Native).
* Stable internet connection.
* MFA (Multi-Factor Authentication) enabled.

## 🛠️ Configuration Steps
1. **Open VPN Client:** Launch the software from the desktop or system tray.
2. **Server Address:** Enter the corporate gateway (e.g., `vpn.companyname.com`).
3. **Authentication:**
   - Enter your **Username** and **Password**.
   - Approve the **MFA notification** on your mobile device.
4. **Verification:** Ensure the status icon turns green and displays "Connected".

## 🔍 Common Troubleshooting (Standard SLA)
| Issue | Potential Cause | Solution |
| :--- | :--- | :--- |
| **Authentication Failed** | Wrong credentials or expired password | Reset password via AD or check Caps Lock. |
| **Connection Timed Out** | Local firewall or weak Wi-Fi | Disable local VPNs and try a wired connection. |
| **MFA Not Received** | Device out of sync or no internet | Check mobile data or re-register the MFA token. |

---
**Author:** Gabriella Costa
**Role:** IT Support Technician / Software Engineering Student
