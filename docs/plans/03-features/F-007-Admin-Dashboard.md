# F-007: Admin Dashboard

---
**Date:** 2025-11-23  
**Audience:** System Administrator, Product Manager, Support Team  
---

## 1. Overview

The **Admin Dashboard** provides comprehensive monitoring and management capabilities for the TailCamp platform. It enables administrators to oversee group health, manage user roles, intervene in stalled projects, and analyze system-wide performance metrics.

**Direct Quote:**
> "시스템 관리 및 모니터링을 위한 관리자 대시보드입니다." ([Features Overview](README.md))

## 2. User Stories

- **US-7.1:** As an **admin**, I want to identify groups that are inactive so that I can intervene and help them get back on track.
- **US-7.2:** As a **support agent**, I want to view a user's assessment history to resolve their support tickets.
- **US-7.3:** As a **manager**, I want to see the overall platform retention rate to gauge business health.

## 3. Functional Requirements (FR)

### FR-1: System Monitoring
- **FR-1.1:** The dashboard shall display real-time statistics on active users, active groups, and completed projects.
- **FR-1.2:** The system shall highlight "At-Risk" groups based on low activity or negative sentiment analysis.

### FR-2: User & Group Management
- **FR-2.1:** Admins shall be able to manually adjust a user's skill level or role.
- **FR-2.2:** Admins shall be able to dissolve a group or reassign members in case of conflicts.

### FR-3: Content Management
- **FR-3.1:** Admins shall be able to update or deprecate project templates.
- **FR-3.2:** Admins shall be able to review and moderate reported content.

## 4. Non-Functional Requirements (NFR)

### NFR-1: Security
- **NFR-1.1:** Access to the Admin Dashboard shall be restricted to users with the `ADMIN` or `SUPER_ADMIN` role.
- **NFR-1.2:** All administrative actions (e.g., banning a user) must be logged in an immutable Audit Log.

### NFR-2: Performance
- **NFR-2.1:** Dashboard widgets shall load within **3 seconds**.
- **NFR-2.2:** Real-time alerts for critical system failures shall be delivered within **1 minute**.

## 5. Interface Specifications

### API Endpoints
- `GET /api/admin/stats`: Retrieves system-wide statistics.
- `POST /api/admin/groups/:id/intervene`: Performs an admin action on a group.
- `GET /api/admin/audit-logs`: Retrieves the audit trail.

*Refer to [API Endpoints](../04-architecture/api-endpoints.md) for detailed schemas.*

## 6. Acceptance Criteria

- [ ] Admin can successfully ban a malicious user.
- [ ] Audit log correctly records the timestamp and actor for a "Group Dissolution" event.
- [ ] "At-Risk" group alert is triggered when a group has no activity for 7 days.

## 7. Related Documents

- [F-007: Risk Assessment](../07-risks/risk-assessment.md)
- [Success Metrics & KPIs](../05-metrics/success-metrics.md)
- [System Architecture](../04-architecture/system-architecture.md)

