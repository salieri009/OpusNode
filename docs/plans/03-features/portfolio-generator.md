# F-006: Portfolio Generator

**Feature ID:** F-006  
**Priority:** P1  
**Phase:** 2  
**Status:** 📋 Planned

---

## 📋 Overview

완료된 프로젝트를 자동으로 분석하여 포트폴리오를 생성하는 시스템입니다. AI가 프로젝트를 요약하고 기술 스택을 추출하여 다양한 템플릿으로 포트폴리오를 생성합니다.

**관련 문서:**
- [Project Workspace](project-workspace.md) - 프로젝트 워크스페이스 (포트폴리오 소스)
- [Features Overview](README.md) - 기능 목록

---

## 👤 User Story

> As a user, I want to automatically generate a portfolio from my projects so that I can showcase my work to employers.

---

## 🎯 Functional Requirements

### 1. Portfolio Generation Process

- **프로젝트 선택** (완료된 프로젝트)
- **AI 자동 요약** (프로젝트 설명)
- **코드 분석 후 기술 스택 정리**
- **이미지/다이어그램 자동 생성** (선택적)

### 2. Template Options

- **Minimal** - 깔끔하고 미니멀한 디자인
- **Dev** - 개발자 친화적 스타일
- **Dark** - 다크 테마
- **Notion Style** - Notion 스타일

### 3. Export Options

- **PDF 다운로드**
- **웹 호스팅** (GitHub Pages 연동)
- **링크 공유**

---

## 🔧 Technical Requirements

### AI/ML Components
- **AI**: GPT-4 for project summarization
- **Code Analysis**: Tree-sitter or similar
- **Image Generation**: DALL-E or Stable Diffusion (선택적)

### Backend
- **PDF Generation**: Puppeteer
- **Hosting**: Vercel/Netlify integration
- **Storage**: AWS S3 (포트폴리오 파일)

### API Endpoints
- `POST /api/portfolio/generate` - 포트폴리오 생성
- `GET /api/portfolio/:id` - 포트폴리오 조회
- `POST /api/portfolio/:id/export` - PDF/웹 내보내기

자세한 API 명세는 [API Endpoints](../04-architecture/api-endpoints.md)를 참조하세요.

---

## ✅ Acceptance Criteria

- [ ] 포트폴리오 생성 시간 2분 이내
- [ ] 기술 스택 추출 정확도 95% 이상
- [ ] PDF 품질 고해상도 지원

---

## ⚠️ Edge Cases

### 프로젝트 데이터 부족
- **프로젝트 설명 없음** → AI 자동 생성
- **코드 없음** → 기술 스택 수동 입력 옵션

### 생성 실패
- **AI API 실패** → 재시도 및 수동 모드
- **PDF 생성 실패** → 웹 버전 우선 제공

---

## 🎨 UX Requirements

### 포트폴리오 생성 화면
- **프로젝트 선택** (체크박스)
- **템플릿 선택** (미리보기)
- **생성 진행률** 표시
- **미리보기** 기능

### 포트폴리오 편집
- **내용 수정** 가능
- **템플릿 변경** 가능
- **섹션 추가/삭제** 가능

자세한 UX 가이드는 [UX/UI Design Principles](../08-design/ux-ui-principles.md)를 참조하세요.

---

## 📊 Success Metrics

- **포트폴리오 생성률**: 완료 프로젝트의 50% 이상
- **기술 스택 정확도**: 95% 이상
- **사용자 만족도**: 4.0/5.0 이상
- **포트폴리오 공유율**: 30% 이상

자세한 메트릭은 [Success Metrics & KPIs](../05-metrics/success-metrics.md)를 참조하세요.

---

## 🔗 관련 문서

- [Project Workspace](project-workspace.md) - 프로젝트 워크스페이스
- [System Architecture](../04-architecture/system-architecture.md) - 기술 아키텍처

---

**다음 단계:** [Admin Dashboard](admin-dashboard.md) 또는 다른 기능 문서 확인

