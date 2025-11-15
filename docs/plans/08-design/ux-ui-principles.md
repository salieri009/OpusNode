# 🎨 UX/UI Design Principles

**Document:** TailCamp PRD - UX/UI Design Principles  
**Version:** 1.0  
**Last Updated:** 2025-11-15

---

## 📋 Overview

TailCamp의 사용자 경험 및 사용자 인터페이스 설계 원칙과 주요 화면 와이어프레임을 정의합니다.

**관련 문서:**
- [Features Overview](../03-features/README.md) - 기능 목록
- [System Architecture](../04-architecture/system-architecture.md) - 시스템 아키텍처

---

## 🎯 Design Philosophy

### Clarity First
복잡한 기능도 직관적으로 이해할 수 있도록 설계합니다.

### Progressive Disclosure
필요한 정보만 단계적으로 노출하여 사용자의 인지 부담을 줄입니다.

### Delightful Moments
작은 애니메이션과 피드백으로 사용자에게 즐거움을 제공합니다.

### Accessibility
WCAG 2.1 AA 준수를 통해 모든 사용자가 접근할 수 있도록 합니다.

---

## 🖼️ Key Screens Wireframe References

### Landing Page

**구성:**
- 히어로 섹션 (제품 소개 + CTA)
- 주요 기능 소개
- 데모 영상
- FAQ

**CTA:** "내 학습 설계받기" 시작 버튼

---

### Onboarding

**단계:**
1. 관심 분야 선택 (멀티 선택)
2. 학습 목표 입력 (자유 텍스트)
3. 수준 진단 시작 버튼

---

### AI Interview

**레이아웃:**
- **좌측**: 채팅 인터페이스
  - 질문 표시
  - 답변 입력 필드
  - 이전 대화 히스토리
- **우측**: 실시간 분석 패널
  - 히트맵 시각화
  - 프로그레스 바
  - 현재 수준 추정

---

### Group Matching

**화면:**
1. **매칭 대기 화면**
   - 애니메이션: "AI가 당신에게 맞는 팀원을 찾고 있어요..."
   - 예상 대기 시간 표시
   - 대기열 순서 (선택적)

2. **매칭 성공 화면**
   - 축하 애니메이션
   - 그룹 구성원 프로필 카드
   - 매칭 기준 투명성 (일치도 %)
   - "상호학습 다짐 카드"

3. **그룹 프로필 페이지**
   - 그룹 정보
   - 구성원 목록
   - 공통 목표

---

### Learning Dashboard

**레이아웃:**
- **상단**: 진행률 바
  - 전체 진행률
  - 분야별 진행률
- **중앙**: 주간 로드맵
  - 주차별 학습 계획
  - Prerequisite 관계 시각화
- **우측**: AI 어시스턴트 위젯
  - "오늘의 미션"
  - 빠른 질문
- **하단**: 그룹 프로젝트 카드
  - 진행 중인 프로젝트
  - 그룹원 진행 상황

---

### Project Workspace

**레이아웃:**
- **좌측**: 프로젝트 정보 및 네비게이션
  - 프로젝트 개요
  - 기술 스택
  - 진행 상태
- **중앙**: 메인 작업 영역
  - 태스크 관리 (드래그 앤 드롭)
  - 파일 공유
  - GitHub 연동
- **우측**: AI 코치 및 채팅
  - AI 코치 챗봇
  - 그룹 채팅

---

## 🎨 Design System

### Color Palette
- **Primary Blue** (`#0a95ff`): Trust, technology
- **Secondary Green** (`#22c55e`): Success, energy
- **Accent Orange** (`#f97316`): Attention, CTAs

### Typography
- **Heading**: Inter, Bold
- **Body**: Inter, Regular
- **Code**: JetBrains Mono

### Components
- Button styles (Primary, Secondary, Ghost)
- Input fields (Text, Textarea, Select)
- Cards (Project, Group, User)
- Modals and Dialogs

---

## ♿ Accessibility

### WCAG 2.1 AA Compliance
- **Color Contrast**: 4.5:1 이상
- **Keyboard Navigation**: 모든 기능 키보드 접근 가능
- **Screen Reader**: ARIA 레이블 및 역할 정의
- **Focus Indicators**: 명확한 포커스 표시

---

## 📱 Responsive Design

### Breakpoints
- **Mobile**: < 768px
- **Tablet**: 768px - 1024px
- **Desktop**: > 1024px

### Mobile-First Approach
모든 디자인은 모바일을 우선으로 설계하고, 데스크톱으로 확장합니다.

---

## 🔗 관련 문서

- [Features Overview](../03-features/README.md) - 기능 목록
- [System Architecture](../04-architecture/system-architecture.md) - 시스템 아키텍처

---

**다음 단계:** [Security & Privacy](../09-security/security-privacy.md) 확인

