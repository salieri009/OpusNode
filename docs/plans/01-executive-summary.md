# 📌 Executive Summary

**Document:** TailCamp PRD - Executive Summary  
**Version:** 1.0  
**Last Updated:** 2025-11-15

---

## 📋 Overview

**TailCamp**는 AI 기반 개인 맞춤형 학습 경로 설계와 협업 그룹 매칭을 통해 실전 프로젝트 중심 학습을 제공하는 플랫폼입니다. 사용자는 AI 인터뷰를 통해 수준을 진단받고, 유사한 목표를 가진 학습자들과 자동으로 매칭되어 그룹 프로젝트를 진행하며 포트폴리오를 구축합니다.

---

## 🎯 핵심 가치 제안

1. **파편화된 학습 자료를 개인화된 학습 로드맵으로 변환**  
   AI가 무수한 튜토리얼, 강의, 문서를 분석하여 개인의 수준과 목표에 맞는 구조화된 학습 경로를 제공합니다.

2. **AI 기반 그룹 매칭으로 최적의 협업 파트너 발견**  
   유사한 목표와 수준의 학습자를 자동으로 매칭하여 효과적인 협업 환경을 조성합니다.

3. **실전 프로젝트 중심 학습으로 포트폴리오 자동 생성**  
   그룹 프로젝트를 통해 실전 경험을 쌓고, 완료된 프로젝트를 자동으로 포트폴리오로 변환합니다.

---

## 📊 비즈니스 목표

### 단기 목표 (6개월)
- **10,000명 활성 사용자** 달성
- **그룹 프로젝트 완료율 70% 이상**
- **사용자 만족도(NPS) 50+** 달성

### 중장기 목표 (12개월)
- **50,000명 활성 사용자**
- **2,000개 활성 학습 그룹**
- **포트폴리오 생성률 50% 이상**

---

## 🎯 타겟 시장

### Primary Personas
1. **Career Switcher (30%)** - 비개발 직종에서 개발로 전환 희망
2. **Skill Upgrader (40%)** - 주니어 개발자 또는 학생
3. **Hobby Learner (20%)** - 개발 취미 또는 사이드 프로젝트 관심
4. **Portfolio Builder (10%)** - 취업 준비생, 신입 개발자

자세한 내용은 [Product Overview](02-product-overview.md)를 참조하세요.

---

## 🚀 핵심 기능

### MVP (Phase 1)
- ✅ AI Interview & Assessment System
- ✅ Group Matching Algorithm
- ✅ Learning Dashboard
- ✅ Basic Project Workspace

### Post-MVP (Phase 2)
- 🔄 Full Project Workspace with GitHub Integration
- 🔄 AI Coach Chatbot
- 🔄 Portfolio Generator
- 🔄 Gamification Elements

자세한 기능 명세는 [Features Overview](03-features/README.md)를 참조하세요.

---

## 🏗️ 기술 스택

- **Frontend**: Next.js 14+, TypeScript, Tailwind CSS
- **Backend**: NestJS, GraphQL + REST API
- **AI**: OpenAI GPT-4 / Claude 3.5, LangChain
- **Database**: PostgreSQL, Redis, Vector DB (Milvus/Pinecone)

자세한 아키텍처는 [System Architecture](04-architecture/system-architecture.md)를 참조하세요.

---

## 📅 개발 일정

### Phase 1: MVP (Months 1-3)
- Month 1: Foundation (프로젝트 셋업, 인증, 기본 DB)
- Month 2: Core Features (AI 인터뷰, 매칭, 대시보드)
- Month 3: Polish & Launch (커리큘럼, 워크스페이스, UI/UX)

### Phase 2: Enhancement (Months 4-6)
- 프로젝트 워크스페이스 완성, AI 코치, 포트폴리오 생성기

자세한 로드맵은 [Development Roadmap](06-roadmap/development-roadmap.md)을 참조하세요.

---

## ⚠️ 주요 리스크

### 기술적 리스크
- AI 평가 정확도 부족 (Medium Probability, High Impact)
- 매칭 알고리즘 성능 이슈 (Low Probability, High Impact)

### 제품 리스크
- 사용자 이탈률 높음 (Medium Probability, High Impact)
- 그룹 해체율 높음 (Medium Probability, High Impact)

자세한 리스크 분석은 [Risk Assessment](07-risks/risk-assessment.md)를 참조하세요.

---

## 📈 성공 지표

### North Star Metric
**활성 학습 그룹 수 (Active Learning Groups)**  
정의: 주간 3회 이상 활동하는 그룹 수  
목표: 6개월 내 2,000개 그룹

### Key Metrics
- **Engagement**: DAU, WAU, 세션 길이, 재방문율
- **Learning**: 인터뷰 완료율, 매칭 성공률, 프로젝트 완료율
- **Quality**: 사용자 만족도, AI 평가 정확도, 매칭 만족도

자세한 메트릭은 [Success Metrics & KPIs](05-metrics/success-metrics.md)를 참조하세요.

---

## 🔗 관련 문서

- [Product Overview](02-product-overview.md) - 비전 및 타겟 오디언스
- [Features Overview](03-features/README.md) - 기능 명세
- [System Architecture](04-architecture/system-architecture.md) - 기술 아키텍처
- [Development Roadmap](06-roadmap/development-roadmap.md) - 개발 계획

---

**다음 단계:** [Product Overview](02-product-overview.md) 읽기

