---
# 🧪 Testing & Verification - TECHNOVA Linux System

---

## 📌 Overview

This document describes the steps used to verify that the TECHNOVA Linux User Management & Security Automation system is working correctly.

Each component is tested to ensure proper configuration, security, and functionality.

---

## 👥 1. User Verification

Check if users are successfully created:

```bash
cat /etc/passwd
````

👉 Verify:

* All department users exist
* Naming convention is correct

---

## 👨‍👩‍👧 2. Group Verification

Check if groups are created and mapped correctly:

```bash id="n0h5mb"
cat /etc/group
```

👉 Verify:

* Department groups exist
* Users are assigned to correct groups

---

## 📁 3. Directory Verification

Check directory structure and permissions:

```bash id="d4f1o6"
ls -ld /company/*
```

👉 Verify:

* All department directories exist
* Permissions are set to `770`
* Group ownership is correct

---

## 🔐 4. Permission Testing

Login as different users and test access:

```bash id="p7k9m1"
su - hr01
cd /company/hr        # Should work
cd /company/admin     # Should be denied
```

👉 Verify:

* User can access only their department
* Access to other departments is restricted

---

## 💾 5. Backup Verification

Check if backup is working:

```bash id="v3k8t2"
ls /backup/home
```

👉 Verify:

* Files from `/home` are copied
* Backup updates periodically

---

## ⏰ 6. Cron Job Verification

Check scheduled tasks:

```bash id="z1p6c4"
crontab -l
```

👉 Verify:

* Backup job exists
* Timing is correct (every 30 minutes)

---

## ⏳ 7. Account Expiry Verification

Check expiry settings:

```bash id="k2j5w8"
chage -l interns01
```

👉 Verify:

* Expiry date is set
* Account becomes inactive after expiry

---

## 📂 8. /etc/skel Verification

Create a new user:

```bash id="m8t3y7"
useradd testuser
```

Check home directory:

```bash id="r5c1q9"
ls /home/testuser
```

👉 Verify:

* `INSTRUCTIONS.txt` exists
* Default files are copied

---

## 🖥️ 9. Login Banner Verification

Login as any user:

```bash id="g6w4p2"
su - adm01
```

👉 Verify:

* Security banner is displayed
* User and system information is shown

---

## 🔄 Testing Flow

```id="u9v2r6"
User Creation
     ↓
User Verification
     ↓
Group Verification
     ↓
Directory & Permission Check
     ↓
Backup Verification
     ↓
Cron Verification
     ↓
Account Expiry Check
     ↓
Final Validation
```

---

## ✅ Final Validation Checklist

* ✔️ Users created correctly
* ✔️ Groups assigned properly
* ✔️ Directory permissions enforced
* ✔️ Backup system working
* ✔️ Cron job scheduled
* ✔️ Account expiry applied
* ✔️ Default user environment configured

---

## 🎯 Conclusion

All components of the TECHNOVA system have been tested and verified successfully.

The system ensures:

* Secure user access
* Controlled permissions
* Automated backup
* Proper account lifecycle management

---

```
