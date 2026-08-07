# Database Design

**Version:** v1.1.2  
**Last Updated:** 2026-08-05

---

# 1. Overview

This document describes the database design of the JBOD Validation Platform.

The system currently uses SQLite as the default database. The database schema is designed with modularity and scalability in mind, allowing future migration to MySQL or PostgreSQL with minimal modifications.

---

# 2. Database Architecture

```
                    +----------------------+
                    |        User          |
                    +----------+-----------+
                               |
                               |
                               ▼
                    +----------------------+
                    |     Execute Job      |
                    +----------+-----------+
                               |
                +--------------+--------------+
                |                             |
                ▼                             ▼
        Test Plan                      Execute Log
                |
                ▼
          Test Case
                |
                ▼
          JBOD Model
                |
                ▼
            Firmware
```

---

# 3. Entity Relationship

```
Firmware
    ▲
    │
    │
JBOD Model
    │
    ▼
Test Plan
    │
    ▼
Test Case

Test Plan
    │
    ▼
Execute Job
    │
    ▼
Execute Log
```

---

# 4. Table Design

## User

Purpose

Manage user accounts and authentication.

Main Information

- Username
- Password
- Email
- Last Login
- Permission

---

## JBOD Model

Purpose

Store all supported JBOD models.

Main Fields

| Field | Description |
|--------|-------------|
| model_name | Model Name |
| vendor | Vendor |
| platform | Hardware Platform |
| description | Description |
| status | Current Status |

Relationship

- Many-to-Many → Firmware

---

## Firmware

Purpose

Manage firmware versions.

Main Fields

| Field | Description |
|--------|-------------|
| firmware_type | Firmware Type |
| version | Version |
| vendor | Vendor |
| build_number | Build Number |
| release_date | Release Date |
| status | Status |

Relationship

- Many-to-Many ← JBOD Model

---

## Test Case

Purpose

Store validation test items.

Main Fields

- Test Name
- Category
- Description
- Expected Result
- Status

---

## Test Plan

Purpose

Organize multiple test cases into a validation plan.

Main Fields

- Plan Name
- Description
- Version
- Status

Relationship

- Contains Multiple Test Cases

---

## Execute Job

Purpose

Record every validation execution.

Current Fields

- Test Plan
- Status
- Start Time
- End Time

Future Fields

- Progress
- Current Step
- Result
- Duration

---

## Execute Log

Purpose

Store execution logs.

Future Fields

- Execute Job
- Timestamp
- Log Level
- Message

---

# 5. Database Relationships

```
Firmware

        ▲

        │

JBOD Model

        │

        ▼

Test Plan

        │

        ▼

Test Case

        │

        ▼

Execute Job

        │

        ▼

Execute Log
```

---

# 6. Current Database Status

| Table | Status |
|--------|:------:|
| User | ✅ |
| JBOD Model | ✅ |
| Firmware | ✅ |
| Test Case | ✅ |
| Test Plan | ✅ |
| Execute Job | 🟡 |
| Execute Log | 🔴 Planned |

---

# 7. Future Expansion

Version v1.2.0

- Execute Log
- Validation Result
- Python Script Result
- Progress Tracking

Version v1.3.0

- Hardware Information
- SSH Configuration
- Validation Server
- Scheduler

Version v2.0.0

- REST API
- Notification
- Report Database

---

# 8. Database Design Principles

The database follows these principles.

- Data Normalization
- Low Coupling
- High Cohesion
- Scalability
- Maintainability
- Referential Integrity

---

# Revision History

| Version | Description |
|----------|-------------|
| v1.1.2 | Initial Database Design |