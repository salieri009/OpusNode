# F-001: AI Interview & Assessment System

---
**Date:** 2025-11-23  
**Audience:** Product Manager, Backend Engineer, AI Engineer  
---

## 1. Overview

The **AI Interview & Assessment System** is a core component designed to evaluate a user's technical proficiency and soft skills through an interactive, chat-based interface. It utilizes Large Language Models (LLMs) to conduct dynamic interviews, analyze responses in real-time, and generate a comprehensive skill profile.

**Direct Quote:**
> "AI 기반 인터뷰를 통해 사용자의 기술 수준을 평가하고 개인화된 학습 경로를 추천하는 시스템입니다." ([Features Overview](README.md))

## 2. User Stories

- **US-1.1:** As a **new user**, I want to take an AI-driven interview so that my current skill level is accurately assessed without bias.
- **US-1.2:** As a **learner**, I want to see a visual representation of my strengths and weaknesses so that I know what to focus on.
- **US-1.3:** As a **system**, I need to handle interruptions gracefully so that users can resume their assessment later.

## 3. Functional Requirements (FR)

### FR-1: Interactive Interview Interface
- **FR-1.1:** The system shall provide a chat interface that simulates a technical interview.
- **FR-1.2:** The system shall ask 8-12 adaptive questions based on the user's previous answers.
- **FR-1.3:** The system shall support both multiple-choice and open-ended questions.

### FR-2: Real-time Analysis
- **FR-2.1:** The system shall analyze user input in real-time to extract keywords and technical concepts.
- **FR-2.2:** The system shall visualize the estimated skill level using a heatmap or progress bar during the interview.

### FR-3: Assessment Scoring
- **FR-3.1:** The system shall generate a JSON-based score profile covering:
    - Backend Engineering
    - Frontend Engineering
    - AI/ML
    - Mobile Development
    - DevOps
- **FR-3.2:** The system shall determine the user's seniority level (Beginner, Junior, Intermediate, Senior, Expert).

### FR-4: Session Management
- **FR-4.1:** The system shall auto-save the interview progress after every interaction.
- **FR-4.2:** The system shall allow users to resume an incomplete interview within 24 hours.

## 4. Non-Functional Requirements (NFR)

### NFR-1: Performance
- **NFR-1.1:** The AI model shall generate a follow-up question within **3 seconds** of user input.
- **NFR-1.2:** The assessment result generation shall complete within **5 seconds** after the final question.

### NFR-2: Reliability
- **NFR-2.1:** The system shall have a fallback mechanism (e.g., GPT-3.5 or cached questions) if the primary LLM service is unavailable.
- **NFR-2.2:** User data must be persisted to the database immediately to prevent data loss during network interruptions.

### NFR-3: Scalability
- **NFR-3.1:** The system shall support up to **1,000 concurrent interview sessions** without performance degradation.

## 5. Interface Specifications

### API Endpoints
- `POST /api/assessment/start`: Initiates a new interview session.
- `POST /api/assessment/answer`: Submits a user response.
- `GET /api/assessment/result/:id`: Retrieves the final assessment report.

*Refer to [API Endpoints](../04-architecture/api-endpoints.md) for detailed schemas.*

## 6. Acceptance Criteria

- [ ] User completes a full interview cycle (Start -> Answer -> Finish) without errors.
- [ ] System correctly classifies a known "Junior" level input as "Junior".
- [ ] Session resumes correctly after a browser refresh.
- [ ] Latency for question generation stays under 3 seconds for 95% of requests.

## 7. Related Documents

- [F-002: Group Matching Algorithm](F-002-Group-Matching.md)
- [F-005: Curriculum Generator](F-005-Curriculum-Generator.md)
- [System Architecture](../04-architecture/system-architecture.md)

