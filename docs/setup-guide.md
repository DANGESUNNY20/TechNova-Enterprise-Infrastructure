
# ⚙️ Setup Guide - TECHNOVA Linux System

---

## 📌 Overview

This guide provides step-by-step instructions to set up the **Linux User Management & Security Automation System** for the TECHNOVA environment.

Ensure you have **root or sudo access** before executing the commands.

---

## 🧱 Step 1: Create Groups

```bash
groupadd admin
groupadd hr
groupadd finance
groupadd it
groupadd sales
groupadd interns
groupadd server
````

---

## 👥 Step 2: Create Users

Example for Admin Department:

```bash
useradd -G admin adm01
useradd -G admin adm02
useradd -G admin adm03
```

👉 Repeat for other departments using naming conventions:

* hr01–hr10
* fin01–fin15
* it01–it12
* sales01–sales23
* interns01–interns20

---

## 🔑 Step 3: Set Passwords

```bash
passwd adm01
passwd hr01
passwd fin01
```

👉 Set strong passwords for all users.

---

## 📁 Step 4: Create Directory Structure

```bash
mkdir -p /company/{admin,finance,hr,interns,it,sales,server,shared}
```

---

## 🔐 Step 5: Assign Ownership & Permissions

```bash
chown :admin /company/admin
chown :finance /company/finance
chown :hr /company/hr
chown :interns /company/interns
chown :it /company/it
chown :sales /company/sales
chown :server /company/server
```

```bash id="i6k3wb"
chmod 770 /company/admin
chmod 770 /company/finance
chmod 770 /company/hr
chmod 770 /company/interns
chmod 770 /company/it
chmod 770 /company/sales
chmod 770 /company/server
```

Shared directory:

```bash id="g8r6pa"
chmod 1777 /company/shared
```

---

## 🔐 Step 6: Apply Password Policy

```bash id="0g6mrl"
chage -M 1 adm01
chage -M 1 hr01
chage -M 1 fin01
```

👉 Forces password expiry (demo purpose).

---

## 💾 Step 7: Configure Backup Automation

Create backup directory:

```bash id="k3f2lm"
mkdir -p /backup/home
```

Edit crontab:

```bash id="3y2pda"
crontab -e
```

Add:

```bash id="u6s9fj"
*/30 * * * * /usr/bin/rsync -av /home/ /backup/home/ >> /var/log/home-backup.log 2>&1
```

---

## ⏳ Step 8: Set Account Expiry (Interns)

```bash id="q2k4vz"
usermod -e 2026-07-27 interns01
usermod -e 2026-07-27 interns02
```

---

## 🖥️ Step 9: Configure Global Login Banner

Edit file:

```bash id="4a7n2x"
vim /etc/bashrc
```

Add:

```bash id="7m2dcs"
echo "========================================"
echo " Company: TECHNOVA"
echo " User: $(whoami)"
echo " Department: $(id -gn)"
echo " Date: $(date)"
echo "----------------------------------------"
echo " Unauthorized access is prohibited"
echo "========================================"
```

---

## 📂 Step 10: Configure /etc/skel

```bash id="5p9rkt"
cd /etc/skel
vim INSTRUCTIONS.txt
```

Example content:

```
Welcome to TECHNOVA
Follow security policies
Do not share passwords
```

Set permission:

```bash id="y6k1qs"
chmod 644 INSTRUCTIONS.txt
```

---

## 🔄 Setup Flow

```id="i9z8yo"
Groups → Users → Passwords → Directories → Permissions → Backup → Expiry → Configuration
```

---

## ✅ Final Check

Verify setup:

```bash id="9m2cxf"
ls /home
cat /etc/passwd
cat /etc/group
ls -ld /company/*
```

---

## 🎯 Conclusion

The system is now fully configured with:

* User and group management
* Secure directory permissions
* Password policy enforcement
* Automated backup system
* Account lifecycle management

---

```

---
