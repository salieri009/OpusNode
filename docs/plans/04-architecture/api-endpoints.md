# 🔌 API Endpoints

**Document:** TailCamp PRD - API Endpoints  
**Version:** 1.0  
**Last Updated:** 2025-11-15

---

## 📋 Overview

TailCamp의 REST API 및 GraphQL 엔드포인트 명세입니다.

**관련 문서:**
- [System Architecture](system-architecture.md) - 시스템 아키텍처
- [Database Schema](database-schema.md) - 데이터베이스 스키마

---

## 🔐 Authentication

### POST /api/auth/register
회원가입

**Request:**
```json
{
  "email": "user@example.com",
  "name": "John Doe",
  "password": "password123"
}
```

**Response:**
```json
{
  "user": {
    "id": "uuid",
    "email": "user@example.com",
    "name": "John Doe"
  },
  "token": "jwt_token"
}
```

---

### POST /api/auth/login
로그인

**Request:**
```json
{
  "email": "user@example.com",
  "password": "password123"
}
```

**Response:**
```json
{
  "user": {
    "id": "uuid",
    "email": "user@example.com",
    "name": "John Doe"
  },
  "token": "jwt_token"
}
```

---

### POST /api/auth/refresh
토큰 갱신

**Headers:**
```
Authorization: Bearer <refresh_token>
```

**Response:**
```json
{
  "token": "new_jwt_token"
}
```

---

## 🧠 Assessment

### POST /api/assessment/start
인터뷰 시작

**Headers:**
```
Authorization: Bearer <token>
```

**Response:**
```json
{
  "session_id": "uuid",
  "question": {
    "id": "q1",
    "text": "What is your experience with backend development?",
    "type": "open-ended"
  }
}
```

---

### POST /api/assessment/answer
답변 제출

**Request:**
```json
{
  "session_id": "uuid",
  "question_id": "q1",
  "answer": "I have 2 years of experience..."
}
```

**Response:**
```json
{
  "next_question": {
    "id": "q2",
    "text": "...",
    "type": "multiple-choice"
  },
  "progress": 0.3
}
```

---

### GET /api/assessment/result/:id
결과 조회

**Response:**
```json
{
  "user_id": "uuid",
  "assessment_date": "2024-12-19T00:00:00Z",
  "scores": {
    "backend": 0.7,
    "frontend": 0.2
  },
  "level": "intermediate",
  "recommended_paths": ["backend_focused"]
}
```

---

## 👥 Matching

### POST /api/matching/join-queue
매칭 대기열 참가

**Request:**
```json
{
  "goals": ["backend", "api_design"],
  "preferred_group_size": 4
}
```

**Response:**
```json
{
  "queue_position": 5,
  "estimated_wait_time": "2 hours"
}
```

---

### GET /api/matching/status
매칭 상태 조회

**Response:**
```json
{
  "status": "waiting",
  "queue_position": 3,
  "estimated_wait_time": "1 hour"
}
```

**Status Values:**
- `waiting`: 대기 중
- `matching`: 매칭 중
- `matched`: 매칭 완료
- `failed`: 매칭 실패

---

### POST /api/matching/leave-queue
대기열 이탈

**Response:**
```json
{
  "message": "Successfully left queue"
}
```

---

## 👥 Groups

### GET /api/groups/:id
그룹 정보 조회

**Response:**
```json
{
  "id": "uuid",
  "name": "Backend Learners",
  "status": "active",
  "members": [
    {
      "id": "uuid",
      "name": "John Doe",
      "role": "leader"
    }
  ]
}
```

---

### GET /api/groups/:id/members
그룹원 조회

**Response:**
```json
{
  "members": [
    {
      "id": "uuid",
      "name": "John Doe",
      "role": "leader",
      "joined_at": "2024-12-19T00:00:00Z"
    }
  ]
}
```

---

### POST /api/groups/:id/leave
그룹 이탈

**Response:**
```json
{
  "message": "Successfully left group"
}
```

---

## 🛠️ Projects

### POST /api/projects
프로젝트 생성

**Request:**
```json
{
  "group_id": "uuid",
  "name": "E-commerce API",
  "description": "RESTful API for e-commerce",
  "tech_stack": ["Node.js", "PostgreSQL"]
}
```

**Response:**
```json
{
  "id": "uuid",
  "name": "E-commerce API",
  "status": "planning"
}
```

---

### GET /api/projects/:id
프로젝트 조회

**Response:**
```json
{
  "id": "uuid",
  "name": "E-commerce API",
  "description": "...",
  "tech_stack": ["Node.js", "PostgreSQL"],
  "status": "in_progress",
  "tasks": [...]
}
```

---

### PUT /api/projects/:id
프로젝트 수정

**Request:**
```json
{
  "name": "Updated Name",
  "status": "in_progress"
}
```

---

### POST /api/projects/:id/tasks
태스크 추가

**Request:**
```json
{
  "title": "Implement authentication",
  "description": "...",
  "assignee_id": "uuid",
  "priority": "high"
}
```

---

## 📚 Curriculum

### GET /api/curriculum/:userId
커리큘럼 조회

**Response:**
```json
{
  "roadmap": {
    "weeks": [
      {
        "week": 1,
        "goals": ["Learn basics"],
        "tasks": [...]
      }
    ]
  },
  "current_week": 1
}
```

---

### PUT /api/curriculum/:userId/progress
진행률 업데이트

**Request:**
```json
{
  "week": 1,
  "completed_tasks": ["task1", "task2"]
}
```

---

## 🎨 Portfolio

### POST /api/portfolio/generate
포트폴리오 생성

**Request:**
```json
{
  "project_ids": ["uuid1", "uuid2"],
  "template": "minimal"
}
```

**Response:**
```json
{
  "id": "uuid",
  "status": "generating",
  "estimated_time": "2 minutes"
}
```

---

### GET /api/portfolio/:id
포트폴리오 조회

**Response:**
```json
{
  "id": "uuid",
  "template": "minimal",
  "content": {...},
  "public_url": "https://..."
}
```

---

### POST /api/portfolio/:id/export
PDF/웹 내보내기

**Request:**
```json
{
  "format": "pdf"
}
```

**Response:**
```json
{
  "download_url": "https://...",
  "expires_at": "2024-12-20T00:00:00Z"
}
```

---

## 🔒 Error Handling

### Error Response Format
```json
{
  "error": {
    "code": "ERROR_CODE",
    "message": "Error message",
    "details": {}
  }
}
```

### Common Error Codes
- `400`: Bad Request
- `401`: Unauthorized
- `403`: Forbidden
- `404`: Not Found
- `500`: Internal Server Error

---

## 📊 Rate Limiting

- **Authentication**: 5 requests/minute
- **Assessment**: 10 requests/minute
- **Matching**: 3 requests/hour
- **General API**: 100 requests/minute

---

## 🔗 관련 문서

- [System Architecture](system-architecture.md) - 시스템 아키텍처
- [Database Schema](database-schema.md) - 데이터베이스 스키마
- [Security & Privacy](../09-security/security-privacy.md) - 보안 및 개인정보 보호

---

**다음 단계:** [Success Metrics & KPIs](../05-metrics/success-metrics.md) 또는 다른 섹션 확인

