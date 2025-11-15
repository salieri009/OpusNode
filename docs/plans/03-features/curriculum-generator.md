# F-005: Personalized Curriculum Generator

**Feature ID:** F-005  
**Priority:** P1  
**Phase:** 1  
**Status:** 📋 Planned

---

## 📋 Overview

AI가 공개 학습 자료를 분석하여 개인의 수준과 목표에 맞는 개인화된 커리큘럼을 생성하는 시스템입니다.

**관련 문서:**
- [AI Assessment](ai-assessment.md) - 평가 시스템 (커리큘럼 입력)
- [Learning Dashboard](learning-dashboard.md) - 학습 대시보드 (커리큘럼 표시)

---

## 👤 User Story

> As a user, I want to receive a personalized learning curriculum based on my assessment so that I know what to learn in what order.

---

## 🎯 Functional Requirements

### 1. Curriculum Structure

- **주 단위 학습 계획**
- **각 주차별 목표 및 태스크**
- **Prerequisite 체인 관리**
- **난이도 조절** (사용자 피드백 기반)

### 2. Content Mapping

- **공개 자료** (튜토리얼, 문서, 강의)를 학습 그래프로 변환
- **Vector DB에 임베딩 저장**
- **유사도 기반 추천**

### 3. Adaptive Learning

- **사용자 진행 속도에 맞춰 조절**
- **약점 보완 추가 학습 제공**
- **강점 심화 옵션**

---

## 🔧 Technical Requirements

### AI/ML Components
- **Vector DB**: Milvus or Pinecone
- **Embedding**: OpenAI text-embedding-3-large
- **Graph DB**: Neo4j (선택적, Prerequisite 관계)
- **Content Scraper**: Custom crawler (공개 자료)

### Backend
- **Curriculum Engine**: Python service
- **Content Processing**: NLP pipeline
- **Storage**: PostgreSQL (커리큘럼 메타데이터)

### API Endpoints
- `GET /api/curriculum/:userId` - 커리큘럼 조회
- `PUT /api/curriculum/:userId/progress` - 진행률 업데이트
- `POST /api/curriculum/:userId/regenerate` - 커리큘럼 재생성

자세한 API 명세는 [API Endpoints](../04-architecture/api-endpoints.md)를 참조하세요.

---

## ✅ Acceptance Criteria

- [ ] 커리큘럼 생성 시간 30초 이내
- [ ] Prerequisite 관계 정확도 90% 이상
- [ ] 사용자 만족도 4.0/5.0 이상

---

## ⚠️ Edge Cases

### 콘텐츠 부족
- **특정 분야 자료 부족** → 대체 자료 제안
- **Prerequisite 불명확** → 사용자 확인 요청

### 적응형 학습
- **진행 속도 과다** → 난이도 조절
- **진행 속도 부족** → 보완 학습 제공

---

## 🎨 UX Requirements

### 커리큘럼 표시
- **주차별 카드 뷰**
- **Prerequisite 그래프** (DAG 시각화)
- **진행률 표시**
- **다음 단계 하이라이트**

### 적응형 피드백
- **난이도 조절 버튼**
- **피드백 수집** (너무 쉬움/어려움)
- **커리큘럼 재생성 옵션**

자세한 UX 가이드는 [UX/UI Design Principles](../08-design/ux-ui-principles.md)를 참조하세요.

---

## 📊 Success Metrics

- **커리큘럼 진행률**: 주차별 60% 이상
- **Prerequisite 정확도**: 90% 이상
- **사용자 만족도**: 4.0/5.0 이상
- **커리큘럼 완료율**: 50% 이상

자세한 메트릭은 [Success Metrics & KPIs](../05-metrics/success-metrics.md)를 참조하세요.

---

## 🔗 관련 문서

- [AI Assessment](ai-assessment.md) - 평가 시스템
- [Learning Dashboard](learning-dashboard.md) - 학습 대시보드
- [System Architecture](../04-architecture/system-architecture.md) - 기술 아키텍처

---

**다음 단계:** [Portfolio Generator](portfolio-generator.md) 또는 [Learning Dashboard](learning-dashboard.md) 확인

