# Security & Privacy

**Document:** TailCamp PRD - Security & Privacy  
**Version:** 1.1  
**Last Updated:** 2025-11-23

---

## 1. Overview

This document defines the security requirements and privacy policies for the TailCamp platform, ensuring the protection of user data and compliance with industry standards.

**Related Documents:**
- [System Architecture](../04-architecture/system-architecture.md)
- [Legal Compliance](compliance-legal.md)

---

## 2. Authentication & Authorization

### 2.1 JWT-Based Authentication

-   **Access Token:** Short-lived (15 minutes), contains user ID and role
-   **Refresh Token:** Long-lived (7 days), stored securely, used to obtain new access tokens
-   **Token Rotation:** Automatic refresh before expiration to maintain session

**Implementation:**
```typescript
// Token payload structure
interface TokenPayload {
  userId: string;
  role: 'user' | 'admin' | 'moderator';
  iat: number; // issued at
  exp: number; // expiration
}
```

### 2.2 Role-Based Access Control (RBAC)

| Role | Permissions | Use Case |
|:-----|:------------|:---------|
| **User** | Create projects, join groups, generate portfolios | Standard users |
| **Admin** | All user permissions + user management, content moderation | Platform administrators |
| **Moderator** | User permissions + flag content, warn users | Community managers |

### 2.3 Multi-Factor Authentication (MFA)

-   **Optional for MVP:** Time-based One-Time Password (TOTP) via authenticator apps
-   **Required for:** Admin accounts, users handling sensitive data

---

## 3. API Security

### 3.1 Transport Security

-   **HTTPS Enforcement:** All traffic redirected from HTTP to HTTPS
-   **TLS Version:** 1.3 minimum (1.2 deprecated)
-   **Certificate:** Let's Encrypt with auto-renewal

### 3.2 Rate Limiting

Prevents abuse and DDoS attacks:

| Endpoint Category | Limit | Window |
|:------------------|:------|:-------|
| Authentication (`/api/auth/*`) | 5 requests | per minute |
| Assessment (`/api/assessment/*`) | 10 requests | per minute |
| Matching (`/api/matching/*`) | 3 requests | per hour |
| General API | 100 requests | per minute |

**Implementation:** Redis-based rate limiter with sliding window algorithm.

### 3.3 Input Validation

-   **SQL Injection Prevention:** Use ORM (TypeORM/Prisma) with parameterized queries
-   **XSS Prevention:** React's default escaping + Content Security Policy (CSP)
-   **CSRF Protection:** CSRF tokens for state-changing operations
-   **Request Size Limits:** 10MB max for file uploads, 100KB for JSON payloads

**Content Security Policy (CSP):**
```http
Content-Security-Policy: 
  default-src 'self'; 
  script-src 'self' 'unsafe-inline'; 
  style-src 'self' 'unsafe-inline'; 
  img-src 'self' data: https:; 
  connect-src 'self' https://api.openai.com;
```

---

## 4. Data Security

### 4.1 Password Hashing

-   **Algorithm:** bcrypt or Argon2 (industry standard)
-   **Cost Factor:** bcrypt rounds=12, Argon2 memory=64MB
-   **Salting:** Unique salt per user (automatic with bcrypt/Argon2)

**Never Acceptable:**
-   Plain text passwords
-   Simple hashing (MD5, SHA-1 without salt)
-   Reversible encryption for passwords

### 4.2 Data Encryption

-   **At Rest:** AES-256 for sensitive fields (e.g., email, assessment answers)
-   **In Transit:** TLS 1.3 for all HTTP traffic, encrypted WebSocket connections
-   **Database:** PostgreSQL column-level encryption for PII

### 4.3 Secure Storage

-   **API Keys:** Store in AWS Secrets Manager or environment variables (never in code)
-   **User Files:** S3 with server-side encryption (SSE-S3)
-   **Backups:** Encrypted daily backups to S3 with 30-day retention

---

## 5. Privacy Requirements

### 5.1 GDPR Compliance (EU Users)

**Core Principles:**
-   **Data Minimization:** Collect only necessary information
-   **Purpose Limitation:** Use data only for stated purposes
-   **Storage Limitation:** Delete data when no longer needed

**User Rights Implementation:**

| Right | Implementation | Timeline |
|:------|:---------------|:---------|
| **Access** | "Download My Data" button → JSON export | Month 2 |
| **Erasure** | "Delete Account" → 30-day soft delete → permanent | Month 2 |
| **Portability** | Export in JSON/CSV format | Month 3 |
| **Rectification** | Profile edit page | Month 1 |

### 5.2 Data Retention Policy

| Data Type | Retention | Rationale |
|:----------|:----------|:----------|
| Active user accounts | Indefinite | Ongoing service |
| Deleted accounts | 30 days (soft delete) | Allow recovery |
| Chat logs | 90 days | Debugging, moderation |
| Assessment results | 2 years | User history, ML training |
| Anonymized analytics | 3 years | Business intelligence |

### 5.3 Cookie Policy

-   **Essential Cookies:** Session management (no consent required)
-   **Analytics Cookies:** Mixpanel, Google Analytics (requires consent)
-   **Cookie Banner:** Displayed on first visit, choice persisted

---

## 6. Security Monitoring

### 6.1 Logging & Auditing

**Events to Log:**
-   Authentication attempts (success and failure)
-   Access to sensitive data (admin actions, user data exports)
-   API errors (4xx, 5xx status codes)
-   Security events (suspicious login patterns, rate limit exceeded)

**Log Retention:** 1 year for audit logs, 90 days for application logs

**Tools:** AWS CloudWatch or DataDog for centralized logging

### 6.2 Alerting

| Alert Type | Threshold | Action |
|:-----------|:----------|:-------|
| **Failed Login Attempts** | >5 from same IP in 10 min | Temporary IP ban (1 hour) |
| **API Error Rate** | >5% for 5 minutes | Page on-call engineer |
| **Suspicious Activity** | Admin login from new device | Email verification required |

### 6.3 Vulnerability Management

-   **Dependency Scanning:** Automated via `npm audit` in CI/CD
-   **Penetration Testing:** Annual third-party pentest (post-MVP)
-   **Bug Bounty:** Consider HackerOne program after public launch

---

## 7. Incident Response

### 7.1 Data Breach Procedure

**Timeline:** 72 hours to notify authorities (GDPR requirement)

1.  **Detection** (Hour 0): Automated monitoring or user report
2.  **Containment** (Hour 1-2): Isolate affected systems
3.  **Assessment** (Hour 2-12): Determine scope, affected users
4.  **Notification** (Hour 12-48): Email affected users, notify data protection authority
5.  **Post-Mortem** (Within 7 days): Root cause analysis, preventive measures

### 7.2 Security Contact

-   **Email:** security@tailcamp.io
-   **Response SLA:** 24 hours for critical issues, 72 hours for non-critical

---

**Next Step:** Review [Legal Compliance](compliance-legal.md).

---

## 📋 Overview

TailCamp의 보안 요구사항 및 개인정보 보호 정책을 정의합니다.

**관련 문서:**
- [System Architecture](../04-architecture/system-architecture.md) - 시스템 아키텍처
- [Database Schema](../04-architecture/database-schema.md) - 데이터베이스 스키마

---

## 🔐 Security Requirements

### Authentication & Authorization

**JWT Token 기반 인증**
- Access Token: 15분 유효
- Refresh Token: 7일 유효
- Token rotation 정책

**Role-Based Access Control (RBAC)**
- User: 일반 사용자
- Admin: 관리자
- Staff: 스태프 (선택적)

---

### API Security

**HTTPS 강제**
- 모든 통신 HTTPS 사용
- TLS 1.3 이상

**API Rate Limiting**
- Authentication: 5 requests/minute
- Assessment: 10 requests/minute
- Matching: 3 requests/hour
- General API: 100 requests/minute

**Input Validation**
- 모든 입력 데이터 검증
- SQL Injection 방지 (ORM 사용)
- XSS 방지 (React 기본 보호 + 추가 검증)
- CSRF 토큰

---

### Data Security

**Password Hashing**
- SHA-256 with salt
- bcrypt 또는 Argon2 사용

**데이터 암호화**
- 민감 정보 암호화 (at rest)
- 전송 중 데이터 암호화 (in transit)

**SQL Injection 방지**
- ORM 사용 (TypeORM, Prisma)
- Parameterized queries

**XSS 방지**
- React 기본 보호
- Content Security Policy (CSP)
- 입력 데이터 sanitization

---

## 🔒 Privacy Requirements

### GDPR 준수

**개인정보 수집 최소화**
- 필요한 정보만 수집
- 명시적 동의 요청

**사용자 권리**
- 데이터 접근 권리
- 데이터 삭제 권리 (Right to be forgotten)
- 데이터 수정 권리
- 데이터 이전 권리

**데이터 보관 정책**
- 보관 기간 명시
- 자동 삭제 정책

---

### 데이터 처리

**데이터 분류**
- 공개 데이터
- 내부 데이터
- 민감 데이터 (암호화 필수)

**데이터 접근 제어**
- 최소 권한 원칙
- 접근 로그 기록
- 정기적인 접근 권한 검토

---

## 🛡️ Security Monitoring

### 로깅 및 모니터링
- 인증 실패 로그
- API 오류 로그
- 의심스러운 활동 감지

### 알림 시스템
- 보안 이벤트 알림
- 이상 활동 알림
- 정기적인 보안 리포트

---

## 🔗 관련 문서

- [System Architecture](../04-architecture/system-architecture.md) - 시스템 아키텍처
- [Database Schema](../04-architecture/database-schema.md) - 데이터베이스 스키마
- [API Endpoints](../04-architecture/api-endpoints.md) - API 엔드포인트

---

**다음 단계:** [Appendix](../10-appendix/appendix.md) 확인

