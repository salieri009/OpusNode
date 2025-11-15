# 🎨 Product Features & Requirements

**Document:** TailCamp PRD - Features Overview  
**Version:** 1.0  
**Last Updated:** 2025-11-15

---

## 📋 Overview

이 섹션은 TailCamp의 모든 기능 명세를 포함합니다. 각 기능은 독립적인 문서로 상세히 설명되어 있습니다.

**관련 문서:**
- [Executive Summary](../01-executive-summary.md) - 프로젝트 개요
- [Product Overview](../02-product-overview.md) - 제품 개요

---

## 📊 Feature Matrix (Priority)

| Feature | Priority | Phase | Effort | Impact | Document |
|---------|----------|-------|--------|--------|----------|
| AI Interview & Assessment | P0 | 1 | High | Critical | [F-001](ai-assessment.md) |
| Group Matching Algorithm | P0 | 1 | High | Critical | [F-002](group-matching.md) |
| Learning Dashboard | P0 | 1 | Medium | Critical | [F-003](learning-dashboard.md) |
| Project Workspace | P0 | 2 | High | High | [F-004](project-workspace.md) |
| Personalized Curriculum | P1 | 1 | High | High | [F-005](curriculum-generator.md) |
| Portfolio Generator | P1 | 2 | Medium | Medium | [F-006](portfolio-generator.md) |
| Admin Dashboard | P2 | 3 | Medium | Low | [F-007](admin-dashboard.md) |
| Gamification | P2 | 3 | Low | Medium | (Learning Dashboard 포함) |

**Priority Legend:**
- **P0**: Must Have (MVP) - 반드시 포함되어야 하는 핵심 기능
- **P1**: Should Have (Post-MVP) - MVP 이후 우선적으로 개발
- **P2**: Nice to Have (Future) - 향후 개발 고려

---

## 🎯 Core Features (P0 - MVP)

### F-001: AI Interview & Assessment System
**Priority:** P0 | **Phase:** 1

사용자의 기술 수준을 평가하기 위한 AI 기반 인터뷰 시스템입니다.

**주요 기능:**
- 채팅 기반 인터뷰 인터페이스
- 실시간 분석 및 히트맵 시각화
- 다차원 점수 평가 (Backend, Frontend, AI/ML, Mobile, DevOps)
- 개인화된 학습 경로 추천

**문서:** [AI Interview & Assessment](ai-assessment.md)

---

### F-002: Group Matching Algorithm
**Priority:** P0 | **Phase:** 1

유사한 목표와 수준의 학습자를 매칭하는 AI 기반 알고리즘입니다.

**주요 기능:**
- Cosine Similarity 기반 목표 매칭
- 경험 수준 및 협업 스타일 밸런스 고려
- 최적 그룹 크기 (3-6명)
- 실시간 매칭 알림

**문서:** [Group Matching Algorithm](group-matching.md)

---

### F-003: Learning Dashboard
**Priority:** P0 | **Phase:** 1

개인화된 학습 로드맵과 진행 상황을 표시하는 대시보드입니다.

**주요 기능:**
- 주간/월간 학습 계획
- Prerequisite 관계 시각화
- 그룹 프로젝트 진행 상황
- AI 작업 어시스턴트

**문서:** [Learning Dashboard](learning-dashboard.md)

---

### F-004: Project Workspace
**Priority:** P0 | **Phase:** 2

그룹 프로젝트 협업을 위한 워크스페이스입니다.

**주요 기능:**
- 태스크 관리 및 역할 분배
- GitHub 연동 및 PR 분석
- 파일 공유 및 버전 관리
- AI 코치 챗봇

**문서:** [Project Workspace](project-workspace.md)

---

## 🚀 Enhanced Features (P1 - Post-MVP)

### F-005: Personalized Curriculum Generator
**Priority:** P1 | **Phase:** 1

AI가 공개 학습 자료를 분석하여 개인화된 커리큘럼을 생성합니다.

**주요 기능:**
- 주 단위 학습 계획
- Prerequisite 체인 관리
- 적응형 학습 (진행 속도 조절)
- Vector DB 기반 콘텐츠 매핑

**문서:** [Personalized Curriculum](curriculum-generator.md)

---

### F-006: Portfolio Generator
**Priority:** P1 | **Phase:** 2

완료된 프로젝트를 자동으로 포트폴리오로 변환합니다.

**주요 기능:**
- AI 자동 프로젝트 요약
- 기술 스택 추출
- 다양한 템플릿 스타일
- PDF/웹 호스팅 내보내기

**문서:** [Portfolio Generator](portfolio-generator.md)

---

## 🔧 Administrative Features (P2 - Future)

### F-007: Admin Dashboard
**Priority:** P2 | **Phase:** 3

시스템 관리 및 모니터링을 위한 관리자 대시보드입니다.

**주요 기능:**
- 그룹 상태 모니터링
- 사용자 레벨 재평가
- 프로젝트 템플릿 관리
- 비정상 그룹 감지

**문서:** [Admin Dashboard](admin-dashboard.md)

---

## 📋 Feature Development Status

| Feature ID | Status | Phase | Target Completion |
|------------|--------|-------|-------------------|
| F-001 | 📋 Planned | 1 | Month 2 |
| F-002 | 📋 Planned | 1 | Month 2 |
| F-003 | 📋 Planned | 1 | Month 2 |
| F-004 | 📋 Planned | 2 | Month 3 |
| F-005 | 📋 Planned | 1 | Month 3 |
| F-006 | 📋 Planned | 2 | Month 5 |
| F-007 | 📋 Planned | 3 | Month 6 |

자세한 개발 일정은 [Development Roadmap](../06-roadmap/development-roadmap.md)을 참조하세요.

---

## 🔗 관련 문서

- [Executive Summary](../01-executive-summary.md) - 프로젝트 개요
- [System Architecture](../04-architecture/system-architecture.md) - 기술 아키텍처
- [Development Roadmap](../06-roadmap/development-roadmap.md) - 개발 계획

---

**다음 단계:** 각 기능 문서를 참조하여 상세 명세 확인

