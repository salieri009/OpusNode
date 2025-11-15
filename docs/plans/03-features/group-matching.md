# F-002: Group Matching Algorithm

**Feature ID:** F-002  
**Priority:** P0  
**Phase:** 1  
**Status:** 📋 Planned

---

## 📋 Overview

유사한 목표와 수준의 학습자를 매칭하여 최적의 협업 그룹을 형성하는 AI 기반 알고리즘입니다.

**관련 문서:**
- [AI Assessment](ai-assessment.md) - 평가 시스템 (매칭 입력 데이터)
- [Features Overview](README.md) - 기능 목록

---

## 👤 User Story

> As a user, I want to be matched with learners who have similar goals and skill levels so that we can collaborate effectively on projects.

---

## 🎯 Functional Requirements

### 1. Matching Criteria

- **목표 일치도** (Cosine Similarity) ≥ 0.7
- **경험 수준 차이** ≤ 1 level
- **성향 밸런스** (리더형/빌더형/리서처형 조합)
- **선호 시간대 겹침** (선택적)

### 2. Group Size

- **최소**: 3명
- **최적**: 4-5명
- **최대**: 6명

### 3. Matching Process

- **대기열 시스템** (FIFO with priority boost)
- **매칭 시도 주기**: 1시간마다
- **최대 대기 시간**: 48시간
- **매칭 실패 시**: 개인 학습 모드 제공

### 4. Matching Algorithm Details

**Input:**
```python
{
  "user_id": "uuid",
  "goals": ["backend", "api_design"],
  "level": "intermediate",
  "scores": {...},
  "collaboration_style": "builder",
  "availability": ["weekday_evening", "weekend"],
  "preferred_group_size": 4
}
```

**Algorithm:**
```
1. Filter candidates by level range (±1 level)
2. Calculate goal similarity (Cosine Similarity)
3. Calculate collaboration style balance score
4. Weighted scoring:
   - Goal match: 40%
   - Level compatibility: 30%
   - Style balance: 20%
   - Availability overlap: 10%
5. Select top N candidates
6. Form group if all criteria met
```

### 5. Matching Result UI

- **매칭 성공 애니메이션**
- **그룹 구성원 프로필 카드**
- **매칭 기준 투명성 표시** (일치도 %)
- **"상호학습 다짐 카드"** 표시

---

## 🔧 Technical Requirements

### Matching Engine
- **Language**: Python service (FastAPI)
- **Algorithm**: Scikit-learn (Cosine Similarity)
- **Queue**: Redis Sorted Set

### Real-time Communication
- **WebSocket**: 매칭 알림 전송
- **Notification**: 매칭 성공 시 즉시 알림

### API Endpoints
- `POST /api/matching/join-queue` - 매칭 대기열 참가
- `GET /api/matching/status` - 매칭 상태 조회
- `POST /api/matching/leave-queue` - 대기열 이탈

자세한 API 명세는 [API Endpoints](../04-architecture/api-endpoints.md)를 참조하세요.

---

## ✅ Acceptance Criteria

- [ ] 매칭 성공률 85% 이상 (48시간 내)
- [ ] 그룹 프로젝트 완료율 70% 이상
- [ ] 사용자 만족도 4.0/5.0 이상
- [ ] 매칭 알고리즘 실행 시간 5초 이내

---

## ⚠️ Edge Cases

### 매칭 실패
- **48시간 내 매칭 실패** → 개인 학습 모드 전환 제안
- **사용자 취소** → 대기열에서 제거

### 그룹 관리
- **그룹 해체** → 재매칭 옵션 제공
- **그룹원 이탈** → 자동 보충 매칭 시도
- **그룹원 불참** → 알림 및 대체 옵션

---

## 🎨 UX Requirements

### 매칭 대기 화면
- **애니메이션**: "AI가 당신에게 맞는 팀원을 찾고 있어요..."
- **예상 대기 시간** 표시
- **대기열 순서** 표시 (선택적)

### 매칭 성공 화면
- **축하 애니메이션**
- **그룹 구성원 프로필 카드**
- **매칭 기준 투명성** (일치도 %)
- **"상호학습 다짐 카드"** (서로 비난하지 않기, 매일 진행 공유 등)

자세한 UX 가이드는 [UX/UI Design Principles](../08-design/ux-ui-principles.md)를 참조하세요.

---

## 📊 Success Metrics

- **매칭 성공률**: 85% 이상 (48시간 내)
- **그룹 프로젝트 완료율**: 70% 이상
- **매칭 만족도**: 4.0/5.0 이상
- **그룹 해체율**: 20% 이하

자세한 메트릭은 [Success Metrics & KPIs](../05-metrics/success-metrics.md)를 참조하세요.

---

## 🔗 관련 문서

- [AI Assessment](ai-assessment.md) - 평가 시스템 (매칭 입력)
- [Project Workspace](project-workspace.md) - 프로젝트 워크스페이스 (매칭 후)
- [System Architecture](../04-architecture/system-architecture.md) - 기술 아키텍처

---

**다음 단계:** [Learning Dashboard](learning-dashboard.md) 또는 [Project Workspace](project-workspace.md) 확인

