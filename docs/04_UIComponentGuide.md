# UI Component Guide

**Version:** v1.1.2  
**Last Updated:** 2026-08-07

---

# 1. Overview

The JBOD Validation Platform adopts a reusable UI component architecture to improve consistency, maintainability, and development efficiency.

All common user interface elements are implemented as reusable Django template components.

---

# 2. Design Principles

The UI component library follows these principles:

- Reusability
- Consistency
- Maintainability
- Scalability
- Separation of Concerns

Every page should reuse existing components whenever possible instead of duplicating HTML.

---

# 3. Component Library

| Component | Purpose |
|----------|---------|
| page_header | Standard page title and description |
| stat_card | Dashboard statistic card |
| status_badge | Display system status |
| search_form | Standard search form |
| empty_state | Display empty data placeholder |

---

# 4. Page Header

## Purpose

Displays a consistent page title across the system.

### Parameters

| Parameter | Description |
|-----------|-------------|
| title | Chinese title |
| title_en | English title |
| subtitle | Page description |

### Example

```django
{% include "components/page_header.html" with
    title="Dashboard"
    title_en="Dashboard"
    subtitle="JBOD Validation Platform"
%}
```

---

# 5. Statistic Card

## Purpose

Displays important statistics on the Dashboard.

### Usage

Typical information displayed:

- Models
- Firmware
- Test Cases
- Running Jobs

---

# 6. Status Badge

## Purpose

Provides a unified status display.

Supported status:

| Status | Color |
|---------|-------|
| PASS | Green |
| FAIL | Red |
| RUNNING | Blue |
| PENDING | Gray |

### Example

```django
{% include "components/status_badge.html" with status=job.status %}
```

---

# 7. Search Form

## Purpose

Provides a unified search interface.

### Features

- Keyword Search
- Responsive Layout
- Bootstrap 5 Compatible

### Example

```django
{% include "components/search_form.html" with
    placeholder="Search..."
    keyword=keyword
%}
```

---

# 8. Empty State

## Purpose

Displays a friendly message when no data is available.

### Features

- Custom Message
- Optional Action Button

### Example

```django
{% include "components/empty_state.html" with
    colspan=5
    message="No Data Found"
    button_url="/model/add/"
    button_text="Create Model"
%}
```

---

# 9. Best Practices

Recommended practices:

- Reuse components whenever possible.
- Avoid duplicate HTML.
- Keep UI consistent across all pages.
- Follow Bootstrap 5 standards.
- Keep components simple and reusable.

---

# 10. Future Components

The following reusable components are planned:

- Breadcrumb
- Pagination
- Modal Dialog
- Loading Spinner
- Notification Alert
- Confirm Dialog

---

# Revision History

| Version | Description |
|----------|-------------|
| v1.1.2 | Initial UI Component Guide |