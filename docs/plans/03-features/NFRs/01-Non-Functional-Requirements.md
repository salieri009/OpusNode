# Non-Functional Requirements (NFRs)

**Document:** TailCamp PRD - Non-Functional Requirements  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

This document consolidates the common Non-Functional Requirements (NFRs) extracted from all feature specifications (F-001 through F-007). These requirements apply across the entire TailCamp platform and must be considered during design, development, and testing phases.

**Purpose:**
- Provide a single source of truth for platform-wide quality attributes
- Ensure consistency across all features
- Guide architectural decisions and testing strategies

**Related Documents:**
- [F-001: AI Assessment](F-001-AI-Assessment.md)
- [F-002: Group Matching](F-002-Group-Matching.md)
- [F-003: Learning Dashboard](F-003-Learning-Dashboard.md)
- [F-004: Project Workspace](F-004-Project-Workspace.md)
- [F-005: Curriculum Generator](F-005-Curriculum-Generator.md)
- [F-006: Portfolio Generator](F-006-Portfolio-Generator.md)
- [F-007: Admin Dashboard](F-007-Admin-Dashboard.md)
- [System Architecture](../04-architecture/01-System-Architecture.md)
- [Security & Privacy](../09-security/01-Security-Privacy.md)

---

## 2. Performance Requirements

### 2.1 Response Time

| Component | Requirement | Measurement | Source |
|:----------|:------------|:------------|:-------|
| **AI Question Generation** | ≤ 3 seconds | 95th percentile | F-001 |
| **Assessment Result Generation** | ≤ 5 seconds | After final question | F-001 |
| **Matching Algorithm Batch Processing** | ≤ 5 seconds | For 1,000 users | F-002 |
| **Match Notification Delivery** | ≤ 500ms | Via WebSocket | F-002 |
| **Dashboard Initial Load** | ≤ 2 seconds | First contentful paint | F-003 |
| **Real-time Updates** | ≤ 1 second | WebSocket message delivery | F-003, F-004 |
| **Chat Message Latency** | < 500ms | End-to-end delivery | F-004 |
| **Vector DB Content Search** | ≤ 200ms | Query response time | F-005 |
| **Curriculum Generation** | ≤ 30 seconds | Initial generation | F-005 |
| **Portfolio Generation** | ≤ 2 minutes | Analysis + rendering | F-006 |
| **Admin Dashboard Widgets** | ≤ 3 seconds | Widget load time | F-007 |
| **Critical System Alerts** | ≤ 1 minute | Alert delivery time | F-007 |

### 2.2 Throughput & Concurrency

| Metric | Requirement | Notes |
|:-------|:------------|:------|
| **Concurrent Interview Sessions** | 1,000+ | Without performance degradation | F-001 |
| **Matching Queue Processing** | 1,000 users per batch | Processed within 5 seconds | F-002 |
| **Real-time WebSocket Connections** | 10,000+ | Per server instance | F-004 |
| **API Request Rate** | 100 req/min (general) | Per user, rate-limited | Architecture |

### 2.3 Resource Utilization

- **CPU Usage:** Average < 70% under normal load
- **Memory Usage:** < 80% of allocated resources
- **Database Connection Pool:** Max 100 connections per service
- **Cache Hit Rate:** > 80% for frequently accessed data

---

## 3. Reliability Requirements

### 3.1 Availability

| Service | Target Availability | Downtime Budget (Monthly) |
|:--------|:-------------------|:-------------------------|
| **Core API Services** | 99.9% | 43 minutes |
| **AI Assessment Service** | 99.5% | 3.6 hours |
| **Matching Service** | 99.0% | 7.2 hours |
| **Real-time Chat** | 99.5% | 3.6 hours |
| **Database** | 99.95% | 21.6 minutes |

### 3.2 Fault Tolerance

**NFR-REL-1: Fallback Mechanisms**
- **Requirement:** All critical services must have fallback mechanisms
- **Examples:**
  - Primary LLM (GPT-4) → Fallback (GPT-3.5 or cached questions) | F-001
  - GitHub API rate limits → Exponential backoff with retry | F-004
  - Vector DB unavailable → Cached results or degraded search | F-005

**NFR-REL-2: Data Persistence**
- **Requirement:** User data must be persisted immediately to prevent data loss
- **Implementation:**
  - Auto-save after every interaction (F-001)
  - Database transactions with rollback capability
  - Session state stored in Redis with persistence

**NFR-REL-3: Error Recovery**
- **Requirement:** System must gracefully handle network interruptions
- **Implementation:**
  - Resume incomplete interviews within 24 hours (F-001)
  - Queue messages for offline users (F-004)
  - Automatic retry with exponential backoff

### 3.3 Data Integrity

- **Transaction Consistency:** ACID compliance for critical operations
- **Backup Frequency:** Daily automated backups
- **Recovery Point Objective (RPO):** 24 hours
- **Recovery Time Objective (RTO):** 15 minutes for application rollback

---

## 4. Scalability Requirements

### 4.1 Horizontal Scaling

**NFR-SCAL-1: Stateless Services**
- **Requirement:** API and Core services must be horizontally scalable
- **Implementation:**
  - Stateless API design (JWT tokens, no server-side sessions)
  - Load balancer distribution
  - Database read replicas for read-heavy operations

**NFR-SCAL-2: Queue-Based Processing**
- **Requirement:** Heavy computational tasks must be offloaded to background workers
- **Examples:**
  - Portfolio generation (F-006)
  - Curriculum generation (F-005)
  - Matching algorithm processing (F-002)

### 4.2 Vertical Scaling

- **Database:** Support for read replicas and connection pooling
- **Cache Layer:** Redis cluster for distributed caching
- **File Storage:** S3 with CDN for global content delivery

---

## 5. Security Requirements

### 5.1 Authentication & Authorization

**NFR-SEC-1: Access Control**
- **Requirement:** Role-based access control (RBAC) for all resources
- **Roles:**
  - `USER`: Standard user access
  - `ADMIN`: Administrative access (F-007)
  - `SUPER_ADMIN`: Full system access
- **Implementation:**
  - JWT tokens with 15-minute expiration
  - Refresh tokens with 7-day expiration
  - MFA optional for sensitive accounts

**NFR-SEC-2: Workspace Access**
- **Requirement:** Workspace access strictly limited to group members and admins
- **Implementation:**
  - Group membership verification on every request
  - Row-level security (RLS) in database queries

### 5.2 Data Protection

**NFR-SEC-3: Encryption**
- **In Transit:** TLS 1.3 for all communications
- **At Rest:** AES-256 for sensitive data (passwords, assessment results)
- **Password Hashing:** bcrypt or Argon2 (never plain text)

**NFR-SEC-4: Input Validation**
- **Requirement:** All user inputs must be validated and sanitized
- **Protection Against:**
  - SQL Injection
  - XSS (Cross-Site Scripting)
  - CSRF (Cross-Site Request Forgery)

**NFR-SEC-5: File Upload Security**
- **Requirement:** All file uploads must be scanned for malware
- **Implementation:**
  - Virus scanning before storage (F-004)
  - File type validation
  - Size limits (e.g., 10MB per file)

### 5.3 Audit & Compliance

**NFR-SEC-6: Audit Logging**
- **Requirement:** All administrative actions must be logged in an immutable audit log
- **Logged Events:**
  - User bans, role changes
  - Group dissolution, member reassignment
  - Content moderation actions
- **Retention:** 7 years for compliance

**NFR-SEC-7: Privacy by Design**
- **Requirement:** User profiles shared during matching shall only reveal necessary technical details
- **Implementation:**
  - Sensitive personal information hidden until group confirmation (F-002)
  - GDPR-compliant data minimization

---

## 6. Usability Requirements

### 6.1 Responsive Design

**NFR-USE-1: Mobile Support**
- **Requirement:** All interfaces must be fully responsive and usable on mobile devices
- **Breakpoints:**
  - Mobile: < 768px
  - Tablet: 768px - 1024px
  - Desktop: > 1024px
- **Touch Targets:** Minimum 44x44px for mobile interactions

### 6.2 Accessibility

**NFR-USE-2: WCAG Compliance**
- **Requirement:** Interface must comply with WCAG 2.1 AA standards
- **Requirements:**
  - Color contrast ratio: 4.5:1 for normal text, 3:1 for large text
  - Keyboard navigation for all interactive elements
  - Screen reader support (ARIA labels, semantic HTML)
  - Focus indicators: 2px visible outline

**NFR-USE-3: Internationalization**
- **Requirement:** Support for multiple languages (future enhancement)
- **Initial:** English, Korean, Japanese

### 6.3 User Experience

**NFR-USE-4: Progressive Disclosure**
- **Requirement:** Present only necessary information at each step
- **Implementation:**
  - Onboarding flow: Step-by-step guidance
  - Dashboard: Collapsible sections
  - Advanced features: Hidden until needed

**NFR-USE-5: Error Messages**
- **Requirement:** Clear, actionable error messages
- **Format:**
  - Plain language (no technical jargon)
  - Suggested actions or solutions
  - Error codes for support reference

---

## 7. Quality Requirements

### 7.1 Accuracy

| Component | Accuracy Requirement | Measurement Method |
|:----------|:---------------------|:-------------------|
| **Matching Algorithm** | 70% project completion rate for matched groups | Track completed projects | F-002 |
| **Tech Stack Extraction** | 95% accuracy in identifying frameworks/languages | Manual validation sample | F-006 |
| **Skill Level Classification** | 85% agreement with expert assessment | Human-in-the-loop validation | F-001 |

### 7.2 Content Quality

**NFR-QUAL-1: Content Filtering**
- **Requirement:** Filter out broken links and outdated content
- **Criteria:**
  - Broken links: HTTP 404, 403, timeout
  - Outdated content: > 3 years for fast-moving tech (F-005)
  - Low-quality: User-reported or low engagement metrics

**NFR-QUAL-2: Content Validation**
- **Requirement:** Automatically validate and replace broken resources
- **Implementation:**
  - Periodic link health checks
  - Alternative resource suggestions
  - User feedback integration

### 7.3 Code Quality

- **Test Coverage:** 80% minimum, 95% for critical paths
- **Code Review:** Required for all PRs (1 approval for `dev`, 2 for `main`)
- **Linting:** ESLint + Prettier with Airbnb style guide
- **Type Safety:** TypeScript strict mode enabled

---

## 8. Privacy Requirements

### 8.1 Data Minimization

**NFR-PRIV-1: Minimal Data Sharing**
- **Requirement:** Only share necessary technical details during matching
- **Shared Data:**
  - Technical skills (from assessment)
  - Learning goals
  - Availability windows
- **Hidden Until Confirmed:**
  - Email address
  - Full name
  - Personal preferences

### 8.2 Data Retention

- **Assessment Data:** Retained for 2 years or until account deletion
- **Chat Messages:** Retained for 90 days
- **Project Data:** Retained indefinitely (user-owned)
- **Audit Logs:** Retained for 7 years (compliance)

### 8.3 User Rights (GDPR)

- **Right to Access:** Users can download their data
- **Right to Erasure:** Account deletion removes all personal data
- **Right to Portability:** Data export in JSON format
- **Right to Correction:** Users can update their information

---

## 9. Monitoring & Observability

### 9.1 Metrics Collection

**NFR-MON-1: Key Metrics**
- **Performance:** Response time (p50, p95, p99), throughput
- **Reliability:** Error rate, availability, uptime
- **Business:** Active users, group formation rate, project completion rate

**NFR-MON-2: Alerting**
- **Critical Alerts:** Error rate > 5%, latency > 3s, availability < 99%
- **Warning Alerts:** Error rate > 1%, latency > 1s
- **Delivery:** Slack, email, PagerDuty (for P0 incidents)

### 9.2 Logging

- **Log Levels:** ERROR, WARN, INFO, DEBUG
- **Structured Logging:** JSON format with correlation IDs
- **Log Retention:** 30 days (application logs), 7 years (audit logs)
- **Tools:** DataDog, New Relic, or CloudWatch

---

## 10. Compliance Requirements

### 10.1 Legal Compliance

- **GDPR:** Full compliance for EU users
- **CCPA:** Compliance for California users
- **COPPA:** Minimum age 13+ to avoid COPPA requirements
- **DMCA:** Registered agent and takedown process

### 10.2 Industry Standards

- **SOC 2 Type II:** Target certification (post-MVP)
- **ISO 27001:** Information security management (future)

---

## 11. Testing Requirements

### 11.1 Test Coverage

| Test Type | Coverage Requirement | Tools |
|:----------|:---------------------|:------|
| **Unit Tests** | 80% minimum | Jest |
| **Integration Tests** | Critical paths only | Supertest |
| **E2E Tests** | Core user flows | Playwright |
| **Performance Tests** | Load testing for critical endpoints | k6, Artillery |

### 11.2 Performance Testing

- **Load Testing:** 1,000 concurrent users
- **Stress Testing:** Identify breaking points
- **Endurance Testing:** 24-hour continuous load
- **Spike Testing:** Sudden traffic increases

---

## 12. Documentation Requirements

### 12.1 Technical Documentation

- **API Documentation:** OpenAPI/Swagger specs
- **Architecture Diagrams:** Updated with each major change
- **Runbooks:** Operational procedures for common issues

### 12.2 User Documentation

- **User Guides:** Step-by-step tutorials for key features
- **FAQ:** Common questions and troubleshooting
- **Video Tutorials:** For complex workflows

---

## 13. Deployment Requirements

### 13.1 Deployment Strategy

- **Zero Downtime:** Blue-green deployment for backend
- **Database Migrations:** Reversible, tested on staging
- **Feature Flags:** Gradual rollout for new features
- **Rollback Capability:** 15-minute RTO

### 13.2 Environment Parity

- **Development:** Mirrors production as closely as possible
- **Staging:** Production-like data and infrastructure
- **Production:** Full monitoring and alerting

---

## 14. Related Documents

- [Features Overview](../03-features/README.md) - All feature specifications
- [01-System-Architecture](../04-architecture/01-System-Architecture.md) - System design
- [01-Security-Privacy](../09-security/01-Security-Privacy.md) - Security details
- [05-CI-CD-Pipeline](../04-architecture/05-CI-CD-Pipeline.md) - Deployment process
- [02-NFRs-Design-Integration](02-NFRs-Design-Integration.md) - How NFRs connect to design decisions

---

**Next Step:** Review [02-NFRs-Design-Integration](02-NFRs-Design-Integration.md) to understand how these NFRs are implemented in the design system.

