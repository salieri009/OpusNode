# OpusNode (TailCamp)

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Status](https://img.shields.io/badge/status-개발중-yellow)
![Version](https://img.shields.io/badge/version-0.1.0-orange)

**기술적 정교함과 사용자 친화적 디자인의 만남**

[🇰🇷 한국어](README.ko.md) | [🇺🇸 English](README.en.md) | [🇯🇵 日本語](README.ja.md)

---

## 📋 프로젝트 정보

**프로젝트 유형**: AI 기반 협업 학습 플랫폼  
**플랫폼**: 웹 애플리케이션  
**아키텍처**: 풀스택 모던 웹 애플리케이션

---

## 🚀 개요

**OpusNode (TailCamp)**는 파편화된 학습 자료를 개인화된 학습 로드맵으로 변환하고, 유사한 목표를 가진 학습자들을 매칭하여 협업 프로젝트 중심 학습을 제공하는 AI 기반 학습 플랫폼입니다. 각 사용자는 협업 네트워크의 노드가 되어 함께 성장합니다.

### 핵심 가치 제안

* 🎯 **개인화된 학습 경로**: AI가 산재된 학습 자료를 구조화된 개인 맞춤형 커리큘럼으로 변환
* 👥 **지능형 그룹 매칭**: AI가 유사한 목표와 수준의 학습자를 매칭하여 효과적인 협업 제공
* 🚀 **프로젝트 중심 학습**: 실전 프로젝트 경험과 자동 포트폴리오 생성
* 🤖 **AI 기반 평가**: AI 인터뷰를 통한 종합적인 기술 수준 평가

---

## ✨ 주요 기능

### 🧠 AI 평가 시스템
* 기술 수준 평가를 위한 인터랙티브 AI 인터뷰
* 시각적 진행 표시기가 있는 실시간 분석
* 다차원 점수 (백엔드, 프론트엔드, AI/ML, 모바일, DevOps)
* 개인화된 학습 추천

### 👥 스마트 그룹 매칭
* 목표, 수준, 협업 스타일 기반 AI 매칭 알고리즘
* 최적 그룹 크기 (3-6명)
* 투명한 매칭 기준 표시
* 자동 그룹 생성 및 관리

### 📚 개인화된 커리큘럼
* 주 단위 학습 로드맵
* 선수 과목 관계 추적
* 진행 상황 기반 적응형 학습
* 공개 자료에서의 콘텐츠 매핑

### 🛠️ 프로젝트 워크스페이스
* 협업 프로젝트 관리
* 작업 할당 및 역할 분배
* GitHub 연동 및 자동 PR 분석
* 가이드를 위한 AI 코치 챗봇

### 🎨 포트폴리오 생성기
* 자동 프로젝트 요약
* 기술 스택 추출
* 다양한 템플릿 스타일 (Minimal, Dev, Dark, Notion Style)
* PDF 및 웹 호스팅 내보내기 옵션

### 📊 학습 대시보드
* 시각적 표시기가 있는 진행 상황 추적
* 게이미피케이션 요소 (레벨, 배지, 연속 학습)
* AI 작업 어시스턴트
* 그룹 프로젝트 상태 모니터링

---

## 🎯 프로젝트 목표

* ✅ AI 기반 기술 평가 시스템 구현
* ✅ 지능형 그룹 매칭 알고리즘 구축
* ✅ 개인화된 커리큘럼 생성기 개발
* ✅ 협업 프로젝트 워크스페이스 개발
* ✅ 자동 포트폴리오 생성 기능 활성화
* ✅ 모던하고 반응형 UI/UX 보장
* ✅ 성능 및 확장성 최적화

---

## 🛠️ 기술 스택

### Frontend
![Next.js](https://img.shields.io/badge/Next.js-14+-black?logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-blue?logo=typescript)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.0+-38bdf8?logo=tailwind-css)

* **프레임워크**: Next.js 14+ (App Router)
* **언어**: TypeScript
* **상태 관리**: Recoil / Zustand
* **스타일링**: Tailwind CSS + shadcn/ui
* **실시간**: Socket.io Client

### Backend
![NestJS](https://img.shields.io/badge/NestJS-10.0+-e0234e?logo=nestjs)
![Node.js](https://img.shields.io/badge/Node.js-20+-339933?logo=node.js)

* **프레임워크**: NestJS
* **언어**: TypeScript
* **API**: GraphQL (Apollo) + REST
* **실시간**: Socket.io
* **작업 큐**: Bull (Redis 기반)

### AI & Data
![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4-412991?logo=openai)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15+-336791?logo=postgresql)
![Redis](https://img.shields.io/badge/Redis-7+-dc382d?logo=redis)

* **LLM**: OpenAI GPT-4 / Anthropic Claude 3.5
* **오케스트레이션**: LangChain / LangGraph
* **벡터 DB**: Milvus / Pinecone
* **데이터베이스**: PostgreSQL 15+
* **캐시**: Redis 7+

### Infrastructure
![AWS](https://img.shields.io/badge/AWS-S3-232f3e?logo=amazon-aws)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ed?logo=docker)

* **호스팅**: AWS / Vercel
* **파일 저장소**: AWS S3
* **CI/CD**: GitHub Actions

---

## 🏃 빠른 시작

### 필수 요구사항

* **Node.js** 20+ 설치
* **PostgreSQL** 15+ 설치
* **Redis** 7+ 설치
* **npm** 또는 **yarn** 패키지 관리자

### 설치 및 설정

1. **저장소 클론**
   ```bash
   git clone <repository-url>
   cd OpusNode
   ```

2. **의존성 설치**
   ```bash
   # Frontend
   cd frontend
   npm install
   
   # Backend
   cd ../backend
   npm install
   ```

3. **환경 설정**
   ```bash
   # 환경 파일 복사
   cp .env.example .env
   # .env 파일을 편집하여 설정
   ```

4. **데이터베이스 설정**
   ```bash
   # 마이그레이션 실행
   npm run migrate
   ```

5. **애플리케이션 실행**
   ```bash
   # 개발 모드
   npm run dev
   ```

6. **애플리케이션 접근**
   ```
   Frontend: http://localhost:3000
   Backend API: http://localhost:4000
   ```

---

## 📁 프로젝트 구조

```
OpusNode/
├── frontend/                 # Next.js 프론트엔드 애플리케이션
│   ├── app/                 # App Router 페이지
│   ├── components/          # React 컴포넌트
│   ├── lib/                 # 유틸리티 및 훅
│   └── public/              # 정적 자산
├── backend/                 # NestJS 백엔드 애플리케이션
│   ├── src/
│   │   ├── modules/         # 기능 모듈
│   │   │   ├── assessment/  # AI 평가 모듈
│   │   │   ├── matching/    # 그룹 매칭 모듈
│   │   │   ├── curriculum/  # 커리큘럼 생성기
│   │   │   ├── projects/    # 프로젝트 워크스페이스
│   │   │   └── portfolio/   # 포트폴리오 생성기
│   │   ├── common/          # 공유 유틸리티
│   │   └── config/          # 설정
│   └── test/                # 테스트 파일
├── ai-engine/               # AI 서비스 레이어
│   ├── assessment/          # 평가 엔진
│   ├── matching/            # 매칭 알고리즘
│   └── curriculum/          # 커리큘럼 생성기
├── docs/                    # 문서
│   └── plans/               # 설계 계획 및 PRD
└── README.md                # 이 파일
```

---

## 🎨 디자인 시스템

OpusNode는 현대적인 원칙으로 구축된 포괄적인 디자인 시스템을 특징으로 합니다:

* 🎯 **컴포넌트 기반 아키텍처**: 재사용 가능한 UI 컴포넌트
* 🌈 **디자인 토큰**: 일관된 색상 팔레트 및 타이포그래피
* 📱 **반응형 디자인**: 모바일 우선 접근
* ♿ **접근성**: WCAG 2.1 AA 준수
* 🎭 **다크 모드**: 완전한 테마 지원
* ⚡ **성능**: 최적화된 애니메이션 및 로딩 상태

---

## 📚 문서

| 언어 | 문서 | 설명 |
|------|------|------|
| 🇰🇷 | [한국어](README.ko.md) | 한국어 전체 문서 |
| 🇺🇸 | [English](README.en.md) | 영어 전체 문서 |
| 🇯🇵 | [日本語](README.ja.md) | 일본어 전체 문서 |

### 추가 자료

* [제품 요구사항 문서](docs/plans/TailCamp_PRD.md) - 포괄적인 PRD
* 디자인 시스템 - 시각적 디자인 가이드라인 (준비 중)
* API 문서 - API 엔드포인트 참조 (준비 중)
* 개발 가이드 - 개발 설정 및 가이드라인 (준비 중)

---

## 🗓️ 개발 로드맵

### Phase 1: MVP (1-3개월)
* ✅ AI 인터뷰 및 평가 시스템
* ✅ 그룹 매칭 알고리즘
* ✅ 학습 대시보드
* ✅ 기본 프로젝트 워크스페이스

### Phase 2: 향상 (4-6개월)
* 🔄 프로젝트 워크스페이스 (전체 기능)
* 🔄 AI 코치 챗봇
* 🔄 포트폴리오 생성기
* 🔄 게이미피케이션 요소

### Phase 3: 확장 (7-12개월)
* 📋 고급 AI 기능
* 📋 모바일 앱 (선택적)
* 📋 커뮤니티 기능
* 📋 프리미엄 기능

---

## 🤝 기여하기

기여를 환영합니다! Pull Request를 자유롭게 제출해 주세요.

1. 저장소 포크
2. 기능 브랜치 생성 (`git checkout -b feature/AmazingFeature`)
3. 변경사항 커밋 (`git commit -m 'Add some AmazingFeature'`)
4. 브랜치에 푸시 (`git push origin feature/AmazingFeature`)
5. Pull Request 열기

---

## 📄 라이선스

이 프로젝트는 MIT 라이선스 하에 있습니다. 자세한 내용은 LICENSE 파일을 참조하세요.

---

**학습자를 위해 ❤️로 제작**

*각 사용자가 협업 네트워크의 노드가 되는 모듈식 학습 플랫폼.*

