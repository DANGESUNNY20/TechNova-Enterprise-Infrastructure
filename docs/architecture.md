```markdown
# 🏗️ Architecture Design - TECHNOVA Linux System

---

## 📌 System Overview

This project simulates an enterprise-level Linux infrastructure for a multi-department organization (**TECHNOVA**).

The system is designed to provide:
- Structured user management  
- Secure access control  
- Automated administrative operations  
- Data protection through backup  

Each department operates independently with controlled access to its own resources.

---

## 🧩 Components

The system is built using the following components:

- 👥 **Users**  
  Department-wise users (HR, Finance, Admin, IT, etc.)

- 👨‍👩‍👧 **Groups**  
  Each department has a dedicated Linux group

- 📁 **Directory Structure**  
  Organized under `/company` for logical separation

- 🔐 **Permissions System**  
  Role-Based Access Control using `chmod` and `chown`

- 💾 **Backup System**  
  Automated backup using `rsync`

- ⏰ **Cron Scheduler**  
  Automates backup and system tasks

- ⏳ **Account Lifecycle Management**  
  Handles account expiry (intern users)

---

## 🗂️ Directory Structure

```

/company
├── admin
├── finance
├── hr
├── interns
├── it
├── sales
├── server
└── shared

```

- Each directory is restricted to its department group  
- `/company/shared` is used for collaboration  

---

## 🔄 Workflow

The system follows this structured workflow:

1. Create department groups  
2. Create users and assign to groups  
3. Set user passwords  
4. Create department directories  
5. Assign ownership and permissions  
6. Configure backup using cron  
7. Set account expiry for interns  
8. Apply system-wide configurations  

---

## 📊 Architecture Diagram

```

```
    +---------+
    |  Admin  |
    +----+----+
         |
         v
    +----+----+
    |  Users  |
    +----+----+
         |
         v
    +----+----+
    | Groups  |
    +----+----+
         |
         v
 +-------+--------+
 |  Directories   |
 | (/company/*)   |
 +-------+--------+
         |
         v
    +----+----+
    |Permissions|
    +----+----+
         |
         v
    +----+----+
    | Backup  |
    +----+----+
         |
         v
  +------+------+
  | /backup/home|
  +-------------+

    Users ---> Account Expiry
```

```

---

## 🧠 Design Logic

- Department isolation ensures security  
- Group-based access simplifies management  
- Automation reduces manual work  
- Backup protects critical data  
- Account expiry prevents misuse of inactive accounts  

---
```
