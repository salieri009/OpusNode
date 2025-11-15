# F-001: AI Interview & Assessment System

**Feature ID:** F-001  
**Priority:** P0  
**Phase:** 1  
**Status:** 📋 Planned

---

## 📋 Overview

AI 기반 인터뷰를 통해 사용자의 기술 수준을 평가하고 개인화된 학습 경로를 추천하는 시스템입니다.

**관련 문서:**
- [Features Overview](README.md) - 기능 목록
- [System Architecture](../04-architecture/system-architecture.md) - 기술 아키텍처

---

## 👤 User Story

> As a new user, I want to answer AI interview questions so that the system can assess my skill level and recommend appropriate learning paths.

---

## 🎯 Functional Requirements

### 1. Interview Flow

- **채팅 기반 인터페이스** 제공
- **질문 수**: 8-12개 (분야별 가변)
- **예상 소요 시간**: 10-15분
- **중단 후 재개 가능** (24시간 내)

### 2. Question Types

- **기술 지식 질문** (Multiple Choice / Open-ended)
- **경험 기반 질문** (프로젝트 경험, 협업 경험)
- **목표 및 동기 질문**
- **학습 스타일 질문**

### 3. Real-time Analysis

- 답변 입력 시 **실시간 키워드 추출**
- **수준 추정 히트맵 시각화**
- **프로그레스 바** 표시

### 4. Assessment Output

JSON 형식 점수 스키마:

```json
{
  "user_id": "uuid",
  "assessment_date": "ISO8601",
  "scores": {
    "backend": 0.7,
    "frontend": 0.2,
    "ai_ml": 0.3,
    "mobile": 0.1,
    "devops": 0.4
  },
  "level": "intermediate",
  "project_maturity": 0.6,
  "collaboration_style": "builder",
  "learning_goals": ["career_switch", "portfolio"],
  "recommended_paths": ["backend_focused", "fullstack"]
}
```

### 5. Result Presentation

- **시각적 레벨 표시** (Beginner / Junior / Intermediate / Senior / Expert)
- **강점/약점 분석**
- **추천 학습 분야**

---

## 🔧 Technical Requirements

### AI/ML Components
- **LLM**: GPT-4 or Claude 3.5 (with fallback to GPT-3.5)
- **Intent Classification**: Fine-tuned BERT or similar
- **Response Analysis**: LangChain + Custom prompt engineering

### Storage
- **PostgreSQL**: Assessment results 저장
- **Redis**: Session cache (인터뷰 진행 상태)

### API Endpoints
- `POST /api/assessment/start` - 인터뷰 시작
- `POST /api/assessment/answer` - 답변 제출
- `GET /api/assessment/result/:id` - 결과 조회

자세한 API 명세는 [API Endpoints](../04-architecture/api-endpoints.md)를 참조하세요.

---

## ✅ Acceptance Criteria

- [ ] 사용자가 10분 이내에 인터뷰 완료 가능
- [ ] 인터뷰 중단 후 24시간 내 재개 가능
- [ ] 수준 평가 정확도 80% 이상 (사용자 피드백 기반)
- [ ] 응답 시간 3초 이내

---

## ⚠️ Edge Cases

### 사용자 입력 처리
- **너무 짧은 답변** → 추가 질문 제공
- **모호한 답변** → 명확화 질문 제공
- **기술 분야 잘못 선택** → 재진단 옵션 제공

### 시스템 오류 처리
- **LLM API 실패** → Fallback 모델 사용
- **세션 만료** → 자동 저장 및 복구
- **네트워크 오류** → 오프라인 모드 지원

---

## 🎨 UX Requirements

### 인터뷰 화면
- **좌측**: 채팅 인터페이스
- **우측**: 실시간 분석 패널
  - 히트맵 시각화
  - 프로그레스 바
  - 현재 수준 추정

### 결과 화면
- 레벨 배지 표시
- 강점/약점 차트
- 추천 학습 분야 카드
- 다음 단계 CTA 버튼

자세한 UX 가이드는 [UX/UI Design Principles](../08-design/ux-ui-principles.md)를 참조하세요.

---

## 📊 Success Metrics

- **인터뷰 완료율**: 80% 이상
- **평가 정확도**: 80% 이상 (사용자 피드백 기반)
- **평균 소요 시간**: 12분 이내
- **재개율**: 60% 이상 (중단 후)

자세한 메트릭은 [Success Metrics & KPIs](../05-metrics/success-metrics.md)를 참조하세요.

---

## 🔗 관련 문서

- [Group Matching Algorithm](group-matching.md) - 매칭 알고리즘 (평가 결과 활용)
- [Personalized Curriculum](curriculum-generator.md) - 커리큘럼 생성 (평가 결과 기반)
- [System Architecture](../04-architecture/system-architecture.md) - 기술 아키텍처

---

**다음 단계:** [Group Matching Algorithm](group-matching.md) 또는 [Learning Dashboard](learning-dashboard.md) 확인

