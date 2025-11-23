# F-002: Group Matching Algorithm

---
**Date:** 2025-11-23  
**Audience:** Product Manager, Backend Engineer, Data Scientist  
---

## 1. Overview

The **Group Matching Algorithm** is an AI-driven engine that connects learners with similar goals, complementary skill levels, and compatible collaboration styles to form effective project teams. It minimizes friction and maximizes project completion rates.

**Direct Quote:**
> "유사한 목표와 수준의 학습자를 매칭하는 AI 기반 알고리즘입니다." ([Features Overview](README.md))

## 2. User Stories

- **US-2.1:** As a **learner**, I want to be matched with peers who have similar learning goals so that we stay motivated.
- **US-2.2:** As a **user**, I want to find teammates who are available during the same hours to ensure smooth collaboration.
- **US-2.3:** As a **system**, I need to balance team composition (e.g., Leader, Builder, Researcher) to prevent role conflict.

## 3. Functional Requirements (FR)

### FR-1: Matching Criteria
- **FR-1.1:** The system shall calculate a **Goal Similarity Score** using Cosine Similarity (threshold ≥ 0.7).
- **FR-1.2:** The system shall ensure team members are within **±1 skill level** of each other.
- **FR-1.3:** The system shall prioritize matching users with overlapping availability windows.

### FR-2: Group Composition
- **FR-2.1:** The system shall form groups with a minimum of **3 members** and a maximum of **6 members**.
- **FR-2.2:** The system shall attempt to mix different collaboration styles (Leader, Builder, Researcher) based on assessment data.

### FR-3: Queue Management
- **FR-3.1:** The system shall process the matching queue every **1 hour**.
- **FR-3.2:** The system shall notify users if a match is not found within **48 hours** and offer a solo project option.

## 4. Non-Functional Requirements (NFR)

### NFR-1: Performance
- **NFR-1.1:** The matching algorithm shall process a batch of 1,000 users within **5 seconds**.
- **NFR-1.2:** Match notifications shall be delivered via WebSocket within **500ms** of group formation.

### NFR-2: Accuracy
- **NFR-2.1:** The algorithm shall achieve a **Project Completion Rate** of at least 70% for matched groups.

### NFR-3: Privacy
- **NFR-3.1:** User profiles shared during matching shall only reveal necessary technical details, hiding sensitive personal information until the group is confirmed.

## 5. Interface Specifications

### API Endpoints
- `POST /api/matching/join-queue`: Adds the user to the matching pool.
- `GET /api/matching/status`: Checks current queue status.
- `POST /api/matching/leave-queue`: Removes the user from the pool.

*Refer to [API Endpoints](../04-architecture/api-endpoints.md) for detailed schemas.*

## 6. Acceptance Criteria

- [ ] Algorithm successfully groups 4 users with identical goals and compatible levels.
- [ ] System prevents grouping of users with zero availability overlap.
- [ ] Users receive a push notification immediately upon successful matching.
- [ ] Unmatched users receive a "Solo Mode" suggestion after the timeout period.

## 7. Related Documents

- [F-001: AI Interview & Assessment System](F-001-AI-Assessment.md)
- [F-004: Project Workspace](F-004-Project-Workspace.md)
- [System Architecture](../04-architecture/system-architecture.md)

