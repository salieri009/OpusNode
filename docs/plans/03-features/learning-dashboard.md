# F-003: Learning Dashboard

**Feature ID:** F-003  
**Priority:** P0  
**Phase:** 1  
**Status:** 📋 Planned

---

## 📋 Overview

개인화된 학습 로드맵과 진행 상황을 표시하고, AI 어시스턴트를 통해 학습을 지원하는 대시보드입니다.

**관련 문서:**
- [Features Overview](README.md) - 기능 목록
- [Personalized Curriculum](curriculum-generator.md) - 커리큘럼 생성기

---

## 👤 User Story

> As a user, I want to see my personalized learning roadmap and track my progress so that I know what to learn next.

---

## 🎯 Functional Requirements

### 1. Dashboard Components

#### a. Personal Roadmap
- **주간/월간 학습 계획**
- **단계별 학습 목표**
- **Prerequisite 관계 시각화** (DAG)
- **완료 체크리스트**

#### b. Group Project Area
- **진행 중인 프로젝트 카드**
- **그룹원 진행 상황**
- **다음 마일스톤 표시**

#### c. AI Task Assistant
- **"오늘의 미션"** 위젯
- **일주일 로드맵 미리보기**
- **AI 추천 다음 단계**

#### d. Progress Tracking
- **전체 진행률 프로그레스 바**
- **분야별 진행률** (Backend, Frontend, etc.)
- **스트릭** (연속 학습 일수)
- **레벨업 표시**

### 2. Gamification Elements

- **레벨 시스템** (Lv.1 ~ Lv.50)
- **배지/스탬프 수집**
- **그룹 전체 진행률 표시**
- **리더보드** (선택적, 그룹 내)

### 3. AI Assistant Features

- **"이 부분 이해 안 돼요"** → 즉시 설명
- **"예제 더 줘"** → 미니 문제 제공
- **"다음 단계 추천해줘"** → 맞춤 추천

---

## 🔧 Technical Requirements

### Frontend
- **Framework**: Next.js + Recoil/Zustand
- **Charts**: Recharts or D3.js
- **Real-time**: WebSocket for group updates

### Backend
- **AI**: LangChain for assistant queries
- **API**: REST API for curriculum data

### API Endpoints
- `GET /api/curriculum/:userId` - 커리큘럼 조회
- `PUT /api/curriculum/:userId/progress` - 진행률 업데이트

자세한 API 명세는 [API Endpoints](../04-architecture/api-endpoints.md)를 참조하세요.

---

## ✅ Acceptance Criteria

- [ ] 대시보드 로딩 시간 2초 이내
- [ ] AI 응답 시간 5초 이내
- [ ] 진행률 업데이트 실시간 반영
- [ ] 모바일 반응형 지원

---

## ⚠️ Edge Cases

### 데이터 부족
- **커리큘럼 미생성** → 생성 유도 메시지
- **프로젝트 없음** → 그룹 매칭 유도

### 실시간 동기화
- **다중 디바이스 접속** → 최신 상태 동기화
- **오프라인 모드** → 로컬 캐시 활용

---

## 🎨 UX Requirements

### 대시보드 레이아웃
- **상단**: 진행률 바
- **중앙**: 주간 로드맵
- **우측**: AI 어시스턴트 위젯
- **하단**: 그룹 프로젝트 카드

### 시각화
- **Prerequisite DAG**: 인터랙티브 그래프
- **진행률 차트**: 분야별 스택 차트
- **스트릭 캘린더**: GitHub 스타일

자세한 UX 가이드는 [UX/UI Design Principles](../08-design/ux-ui-principles.md)를 참조하세요.

---

## 📊 Success Metrics

- **커리큘럼 진행률**: 주차별 60% 이상
- **AI 어시스턴트 사용률**: 50% 이상
- **대시보드 방문 빈도**: 주 3회 이상
- **게이미피케이션 참여율**: 70% 이상

자세한 메트릭은 [Success Metrics & KPIs](../05-metrics/success-metrics.md)를 참조하세요.

---

## 🔗 관련 문서

- [Personalized Curriculum](curriculum-generator.md) - 커리큘럼 생성기
- [Group Matching Algorithm](group-matching.md) - 그룹 매칭
- [Project Workspace](project-workspace.md) - 프로젝트 워크스페이스

---

**다음 단계:** [Project Workspace](project-workspace.md) 또는 [Personalized Curriculum](curriculum-generator.md) 확인

