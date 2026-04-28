# 📊 Command Reference - TECHNOVA Linux System

---

## 📌 Overview

This document lists the key Linux commands used in the TECHNOVA User Management & Security Automation project, along with their purpose.

---

## 👥 User Management Commands

### ➤ Create User
```bash
useradd username
````

Creates a new user account.

---

### ➤ Create User with Group

```bash
useradd -G groupname username
```

Creates a user and assigns them to a specific group.

---

### ➤ Set Password

```bash
passwd username
```

Sets or updates the user password.

---

### ➤ Modify User

```bash
usermod options username
```

Used to modify existing user settings.

---

## 👨‍👩‍👧 Group Management Commands

### ➤ Create Group

```bash
groupadd groupname
```

Creates a new group.

---

### ➤ Delete Group

```bash
groupdel groupname
```

Removes a group.

---

## 🔐 Security & Permissions Commands

### ➤ Change Permissions

```bash
chmod permissions file/directory
```

Controls access rights.

Example:

```bash
chmod 770 /company/admin
```

---

### ➤ Change Ownership

```bash
chown user:group file/directory
```

Changes file or directory ownership.

Example:

```bash
chown :admin /company/admin
```

---

### ➤ Password Policy

```bash
chage options username
```

Manages password expiry.

Example:

```bash
chage -M 1 username
```

---

## 💾 Backup & Automation Commands

### ➤ Rsync (Backup)

```bash
rsync -av source destination
```

Used for file synchronization and backup.

Example:

```bash
rsync -av /home/ /backup/home/
```

---

### ➤ Crontab (Scheduler)

```bash
crontab -e
```

Edits cron jobs for task scheduling.

Example:

```bash
*/30 * * * * command
```

---

## 📂 File & Directory Commands

### ➤ Create Directory

```bash
mkdir directory_name
```

Example:

```bash
mkdir -p /company/admin
```

---

### ➤ List Files

```bash
ls
```

Example:

```bash
ls /home
```

---

## 🔍 Verification Commands

### ➤ View Users

```bash
cat /etc/passwd
```

---

### ➤ View Groups

```bash
cat /etc/group
```

---

### ➤ Check User Details

```bash
id username
```

---

### ➤ Check Directory Permissions

```bash
ls -ld directory
```

Example:

```bash
ls -ld /company/admin
```

---

## 📊 Summary

This project utilizes core Linux commands for:

* User and group management
* Security and access control
* Backup and automation
* System verification

---

## 🎯 Conclusion

Understanding and applying these commands is essential for:

* Linux System Administration
* Cybersecurity Operations
* VAPT and Infrastructure Security

---

```

---
