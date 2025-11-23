# F-005: Personalized Curriculum Generator

---
**Date:** 2025-11-23  
**Audience:** Product Manager, AI Engineer, Content Strategist  
---

## 1. Overview

The **Personalized Curriculum Generator** leverages AI to analyze public learning resources and construct a tailored learning path for each user. It adapts to the user's pace and goals, ensuring an efficient upskilling journey.

**Direct Quote:**
> "AI가 공개 학습 자료를 분석하여 개인화된 커리큘럼을 생성합니다." ([Features Overview](README.md))

## 2. User Stories

- **US-5.1:** As a **learner**, I want a curriculum that matches my current skill level so that I am neither bored nor overwhelmed.
- **US-5.2:** As a **user**, I want the curriculum to update if I learn faster than expected.
- **US-5.3:** As a **content manager**, I want the system to automatically index high-quality tutorials from the web.

## 3. Functional Requirements (FR)

### FR-1: Curriculum Generation
- **FR-1.1:** The system shall generate a weekly learning plan based on the user's assessment results (F-001).
- **FR-1.2:** The curriculum shall enforce prerequisite chains (e.g., "Learn HTML" before "Learn React").

### FR-2: Content Mapping
- **FR-2.1:** The system shall use Vector Embeddings to map user goals to specific learning resources (articles, videos).
- **FR-2.2:** The system shall prioritize free and high-rated content.

### FR-3: Adaptive Learning
- **FR-3.1:** The system shall adjust the difficulty of future weeks based on the user's completion speed and quiz performance.
- **FR-3.2:** Users shall be able to manually request "More Advanced" or "Easier" content for specific topics.

## 4. Non-Functional Requirements (NFR)

### NFR-1: Performance
- **NFR-1.1:** Initial curriculum generation shall complete within **30 seconds**.
- **NFR-1.2:** Content search queries against the Vector DB shall return within **200ms**.

### NFR-2: Quality
- **NFR-2.1:** The system shall filter out broken links and outdated content (older than 3 years for fast-moving tech).

## 5. Interface Specifications

### API Endpoints
- `POST /api/curriculum/:userId/generate`: Triggers the generation process.
- `POST /api/curriculum/:userId/regenerate`: Re-calculates the path based on new feedback.

*Refer to [API Endpoints](../04-architecture/api-endpoints.md) for detailed schemas.*

## 6. Acceptance Criteria

- [ ] Generated curriculum respects the logical dependency of topics (DAG check).
- [ ] System successfully replaces a broken link with an alternative resource.
- [ ] User feedback "Too difficult" triggers a regeneration with simplified content.

## 7. Related Documents

- [F-001: AI Interview & Assessment System](F-001-AI-Assessment.md)
- [F-003: Learning Dashboard](F-003-Learning-Dashboard.md)
- [System Architecture](../04-architecture/system-architecture.md)

