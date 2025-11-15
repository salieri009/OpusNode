# 🏗️ System Architecture

**Document:** TailCamp PRD - System Architecture  
**Version:** 1.0  
**Last Updated:** 2025-11-15

---

## 📋 Overview

TailCamp의 전체 시스템 아키텍처와 각 레이어의 역할을 설명합니다.

**관련 문서:**
- [Technology Stack](technology-stack.md) - 기술 스택 상세
- [Database Schema](database-schema.md) - 데이터베이스 스키마
- [API Endpoints](api-endpoints.md) - API 엔드포인트

---

## 🏗️ High-Level Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        Frontend Layer                         │
│  Next.js + TypeScript + Recoil/Zustand + WebSocket Client   │
└──────────────────────┬──────────────────────────────────────┘
                       │
┌──────────────────────┴──────────────────────────────────────┐
│                      API Gateway Layer                       │
│              NestJS + GraphQL + REST API                     │
└──────┬───────────────┬───────────────┬──────────────────────┘
       │               │               │
┌──────┴──────┐ ┌──────┴──────┐ ┌──────┴──────┐
│   Core      │ │   AI        │ │  Matching   │
│   Service   │ │   Engine    │ │  Service    │
└──────┬──────┘ └──────┬──────┘ └──────┬──────┘
       │               │               │
┌──────┴───────────────┴───────────────┴──────┐
│            Data & Storage Layer              │
│  PostgreSQL │ Redis │ Vector DB │ S3 │ GitHub│
└──────────────────────────────────────────────┘
```

---

## 📦 Architecture Layers

### 1. Frontend Layer

**역할:**
- 사용자 인터페이스 제공
- 실시간 업데이트 수신
- 상태 관리 및 라우팅

**주요 컴포넌트:**
- Next.js App Router
- React Components
- State Management (Recoil/Zustand)
- WebSocket Client

**상세:** [Technology Stack](technology-stack.md) 참조

---

### 2. API Gateway Layer

**역할:**
- 요청 라우팅 및 인증
- GraphQL 및 REST API 제공
- Rate Limiting 및 보안

**주요 컴포넌트:**
- NestJS Framework
- GraphQL (Apollo)
- REST API
- Authentication Middleware

---

### 3. Core Service Layer

**역할:**
- 비즈니스 로직 처리
- 데이터 검증 및 변환
- 외부 서비스 연동

**주요 서비스:**
- User Service
- Group Service
- Project Service
- Curriculum Service

---

### 4. AI Engine Layer

**역할:**
- AI 모델 오케스트레이션
- 자연어 처리
- 벡터 검색 및 추천

**주요 컴포넌트:**
- LangChain / LangGraph
- LLM (GPT-4 / Claude 3.5)
- Embedding Model
- Intent Classifier

---

### 5. Matching Service Layer

**역할:**
- 그룹 매칭 알고리즘 실행
- 대기열 관리
- 실시간 매칭 알림

**주요 컴포넌트:**
- Python FastAPI Service
- Matching Algorithm
- Redis Queue
- WebSocket Server

---

### 6. Data & Storage Layer

**역할:**
- 데이터 영구 저장
- 캐싱 및 세션 관리
- 파일 저장

**주요 컴포넌트:**
- PostgreSQL (Primary DB)
- Redis (Cache & Queue)
- Vector DB (Milvus/Pinecone)
- AWS S3 (File Storage)
- GitHub (Code Storage)

**상세:** [Database Schema](database-schema.md) 참조

---

## 🔄 Data Flow

### Assessment Flow
```
User Input → Frontend → API Gateway → AI Engine → LLM API
                ↓
         PostgreSQL (Results)
                ↓
         Redis (Session Cache)
```

### Matching Flow
```
User Join Queue → Matching Service → Algorithm → Redis Queue
                                            ↓
                                    WebSocket Notification
                                            ↓
                                    Group Formation
```

### Project Collaboration Flow
```
User Action → Frontend → API Gateway → Core Service
                                    ↓
                            WebSocket Broadcast
                                    ↓
                            All Group Members
```

---

## 🔐 Security Architecture

### Authentication & Authorization
- JWT Token 기반 인증
- Role-Based Access Control (RBAC)
- API Rate Limiting

### Data Security
- HTTPS 강제
- 데이터 암호화 (민감 정보)
- SQL Injection 방지 (ORM 사용)
- XSS 방지 (React 기본 보호)

**상세:** [Security & Privacy](../09-security/security-privacy.md) 참조

---

## 📊 Scalability Considerations

### Horizontal Scaling
- Stateless API 서버 (로드 밸런싱 가능)
- Redis Cluster (캐시 분산)
- PostgreSQL Read Replicas

### Performance Optimization
- CDN 활용 (정적 자산)
- Database Indexing
- Query Optimization
- Caching Strategy

---

## 🔗 관련 문서

- [Technology Stack](technology-stack.md) - 기술 스택 상세
- [Database Schema](database-schema.md) - 데이터베이스 스키마
- [API Endpoints](api-endpoints.md) - API 엔드포인트
- [Security & Privacy](../09-security/security-privacy.md) - 보안 및 개인정보 보호

---

**다음 단계:** [Technology Stack](technology-stack.md) 또는 [Database Schema](database-schema.md) 확인

