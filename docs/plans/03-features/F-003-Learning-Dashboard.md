# F-003: Learning Dashboard

---
**Date:** 2025-11-23  
**Audience:** Product Manager, Frontend Engineer, UX Designer  
---

## 1. Overview

The **Learning Dashboard** is the central hub for users, visualizing their personalized learning roadmap, tracking progress, and providing AI-assisted guidance. It serves as the primary interface for daily engagement.

**Direct Quote:**
> "개인화된 학습 로드맵과 진행 상황을 표시하는 대시보드입니다." ([Features Overview](README.md))

## 2. User Stories

- **US-3.1:** As a **user**, I want to see a clear weekly plan so that I know exactly what tasks to complete today.
- **US-3.2:** As a **learner**, I want to track my progress across different technical domains (e.g., Backend, Frontend) to ensure balanced growth.
- **US-3.3:** As a **user**, I want to quickly access my group project status to stay aligned with my team.

## 3. Functional Requirements (FR)

### FR-1: Personal Roadmap Visualization
- **FR-1.1:** The system shall display a **Directed Acyclic Graph (DAG)** representing the prerequisite relationships between learning modules.
- **FR-1.2:** The system shall highlight the "Current Week's Tasks" and mark completed items clearly.

### FR-2: Progress Tracking
- **FR-2.1:** The system shall calculate and display an overall completion percentage.
- **FR-2.2:** The system shall track a "Daily Streak" to encourage consistent login and activity.
- **FR-2.3:** The system shall award badges/levels (Gamification) based on completed milestones.

### FR-3: AI Task Assistant
- **FR-3.1:** The dashboard shall include an AI widget that suggests the "Next Best Action" based on current progress.
- **FR-3.2:** The AI assistant shall provide instant explanations for concepts when queried by the user.

## 4. Non-Functional Requirements (NFR)

### NFR-1: Performance
- **NFR-1.1:** The dashboard shall load the initial view (roadmap + progress) within **2 seconds**.
- **NFR-1.2:** Real-time updates (e.g., project notifications) shall appear within **1 second**.

### NFR-2: Usability
- **NFR-2.1:** The dashboard must be fully responsive and usable on mobile devices.
- **NFR-2.2:** The interface shall comply with WCAG 2.1 AA accessibility standards.

## 5. Interface Specifications

### API Endpoints
- `GET /api/curriculum/:userId`: Fetches the full curriculum structure.
- `PUT /api/curriculum/:userId/progress`: Updates the status of a specific learning module.

*Refer to [API Endpoints](../04-architecture/api-endpoints.md) for detailed schemas.*

## 6. Acceptance Criteria

- [ ] Dashboard correctly renders the dependency graph for a complex curriculum.
- [ ] Progress bar updates immediately upon marking a task as complete.
- [ ] AI Assistant widget responds to a "What should I do next?" query with a relevant task.
- [ ] Mobile view correctly stacks the layout without horizontal scrolling.

## 7. Related Documents

- [F-005: Personalized Curriculum Generator](F-005-Curriculum-Generator.md)
- [F-004: Project Workspace](F-004-Project-Workspace.md)
- [UX/UI Design Principles](../08-design/ux-ui-principles.md)

