# Project Structure

**Version:** v1.1.2  
**Last Updated:** 2026-08-05

---

# 1. Overview

This document describes the directory structure of the JBOD Validation Platform.

The project follows Django's modular architecture, where each application is responsible for an independent business domain.

---

# 2. Project Structure

```
JBOD-Validation/
│
├── dashboard/
├── user/
├── models_app/
├── firmware/
├── testcase/
├── testplan/
├── executor/
├── report/
│
├── templates/
├── static/
├── docs/
│
├── manage.py
├── requirements.txt
├── README.md
└── CHANGELOG.md
```

---

# 3. Application Modules

## dashboard/

### Purpose

Provides the system dashboard and overview information.

### Responsibilities

- Dashboard homepage
- Statistics cards
- Recent execution jobs
- Latest firmware information

### Main Files

```
dashboard/
├── views.py
├── urls.py
└── templates/dashboard/
```

---

## user/

### Purpose

Handles user authentication and account management.

### Responsibilities

- Login
- Logout
- User Registration
- Session Management

### Main Files

```
user/
├── views.py
├── forms.py
├── models.py
└── templates/user/
```

---

## models_app/

### Purpose

Manages JBOD product models.

### Responsibilities

- Create Model
- Edit Model
- Delete Model
- Search Model
- Model Details

---

## firmware/

### Purpose

Manages firmware information.

### Responsibilities

- Firmware CRUD
- Firmware Version
- Vendor Information
- Release Date

---

## testcase/

### Purpose

Stores validation test cases.

### Responsibilities

- Test Case CRUD
- Test Item Management

---

## testplan/

### Purpose

Combines multiple test cases into executable validation plans.

### Responsibilities

- Create Test Plan
- Edit Test Plan
- Execute Preparation

---

## executor/

### Purpose

Executes validation jobs.

### Current Responsibilities

- Execute Job
- Job Status
- Execution History

### Future Responsibilities

- Python Script Runner
- Log Collection
- SSH Execution
- Hardware Validation
- Result Analysis

---

## report/

### Purpose

Generates validation reports.

### Planned Features

- PDF Report
- Excel Report
- Validation Summary
- Download Center

---

# 4. Shared Resources

## templates/

Stores all Django HTML templates.

```
templates/

components/
dashboard/
firmware/
models/
testcase/
testplan/
executor/
user/
```

---

## static/

Stores frontend resources.

```
static/

css/
js/
images/
```

---

## docs/

Project documentation.

```
docs/

01_Architecture.md
02_ProjectStructure.md
03_DatabaseDesign.md
04_UIComponentGuide.md
05_DevelopmentPlan.md
```

---

# 5. Root Files

| File | Description |
|------|-------------|
| manage.py | Django management entry point |
| requirements.txt | Python dependencies |
| README.md | Project introduction |
| CHANGELOG.md | Version history |

---

# 6. Design Principles

The project structure follows these principles:

- Modular Architecture
- Low Coupling
- High Cohesion
- Easy Maintenance
- Scalability
- Clear Responsibility Separation

Each Django application should focus on a single business domain.

---

# 7. Future Expansion

The following modules are planned for future versions.

```
Automation Engine

↓

SSH Client

↓

Validation Scripts

↓

Report Generator

↓

REST API

↓

Scheduler
```

---

# Revision History

| Version | Description |
|----------|-------------|
| v1.1.2 | Initial Project Structure documentation |