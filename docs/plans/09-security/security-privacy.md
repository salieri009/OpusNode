# 🔒 Security & Privacy

**Document:** TailCamp PRD - Security & Privacy  
**Version:** 1.0  
**Last Updated:** 2025-11-15

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

