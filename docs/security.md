# 🔐 Security Design - TECHNOVA Linux System

---

## 📌 Overview

This project implements security controls using native Linux mechanisms to ensure:

- Controlled access to system resources  
- Protection of user data  
- Enforcement of security policies  
- Prevention of unauthorized access  

The design focuses on **practical system-level security** aligned with real-world enterprise environments.

---

## 🛡️ Security Components

### 👨‍👩‍👧 1. Role-Based Access Control (RBAC)

RBAC is implemented using Linux groups.

- Each department has a dedicated group  
- Users are assigned only to their respective group  
- Access to directories is controlled based on group membership  

👉 This ensures:
- Department isolation  
- Controlled access to sensitive data  

---

### 📁 2. Directory Permission Control

```bash
chmod 770 /company/<department>
chown :<group> /company/<department>
````

**Permission Breakdown:**

* Owner → Full access
* Group → Full access
* Others → No access

👉 This prevents unauthorized access from other departments.

---

### 🔑 3. Password Policy Enforcement

```bash
chage -M 1 username
```

* Forces password expiry
* Ensures users regularly update credentials

📌 Note:
In real environments, password expiry is typically set to **30–90 days**.
Here it is set to **1 day for demonstration purposes**.

---

### ⏳ 4. Account Expiry Management

```bash
usermod -e YYYY-MM-DD username
```

* Used for temporary users (interns)
* Automatically disables account after expiry date

👉 Prevents:

* Unauthorized long-term access
* Misuse of inactive accounts

---

### 📂 5. Secure User Onboarding (/etc/skel)

* Default files are placed in `/etc/skel`
* Automatically copied to new user home directories

Example:

* `INSTRUCTIONS.txt` with security guidelines

👉 Ensures:

* Standardized environment
* User awareness of security policies

---

### 🖥️ 6. Global Security Banner

Configured in `/etc/bashrc`

Displays:

* User information
* Security warning
* Monitoring notice

👉 Purpose:

* Warn users about system monitoring
* Act as a legal security notice

---

### 💾 7. Backup Security

* Automated using `rsync` and `cron`
* Backup of `/home` directory

👉 Benefits:

* Protects against data loss
* Enables recovery after failure or attack

---

## 🔄 Security Flow

````
User Login
     ↓
Authentication (Password)
     ↓
Authorization (Group Check)
     ↓
Access Control (Permissions)
     ↓
Directory Access
     ↓
Logging & Monitoring
``` id="n9qk9s"

---

## 🧠 Security Justification

- RBAC reduces unauthorized access risk  
- Password policies enforce compliance  
- Account expiry controls temporary access  
- Backup ensures data availability  
- Security banner improves awareness  

---

## 🔒 Conclusion

This system demonstrates how Linux-native tools can be used to implement **effective security controls** in an enterprise environment.

It combines:
- Access control  
- Policy enforcement  
- Automation  
- Data protection  

to create a secure and manageable infrastructure.

---
````

---
