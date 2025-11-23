# F-006: Portfolio Generator

---
**Date:** 2025-11-23  
**Audience:** Product Manager, Frontend Engineer, AI Engineer  
---

## 1. Overview

The **Portfolio Generator** automatically compiles a user's project contributions into a professional-grade portfolio. It analyzes code commits, project descriptions, and role data to generate a showcase that proves practical experience.

**Direct Quote:**
> "완료된 프로젝트를 자동으로 포트폴리오로 변환합니다." ([Features Overview](README.md))

## 2. User Stories

- **US-6.1:** As a **job seeker**, I want to generate a portfolio PDF so that I can attach it to my resume.
- **US-6.2:** As a **developer**, I want my portfolio to highlight the specific technologies I used (e.g., React, NestJS) rather than just generic project info.
- **US-6.3:** As a **user**, I want to choose from different design templates (e.g., Minimal, Dark Mode) to match my personal style.

## 3. Functional Requirements (FR)

### FR-1: Automated Content Generation
- **FR-1.1:** The system shall use LLMs to summarize the project description and the user's specific contributions.
- **FR-1.2:** The system shall analyze the codebase to automatically detect and list the Tech Stack used.

### FR-2: Template System
- **FR-2.1:** The system shall provide at least 4 distinct templates: Minimal, Dev-Centric, Dark Mode, and Notion-Style.
- **FR-2.2:** Users shall be able to customize the layout (e.g., reorder sections, hide specific projects).

### FR-3: Export & Hosting
- **FR-3.1:** The system shall generate a high-resolution PDF export.
- **FR-3.2:** The system shall support one-click deployment to a web-hosted version (e.g., via GitHub Pages or internal hosting).

## 4. Non-Functional Requirements (NFR)

### NFR-1: Performance
- **NFR-1.1:** Portfolio generation (analysis + rendering) shall complete within **2 minutes**.
- **NFR-1.2:** The hosted portfolio page shall have a Lighthouse Performance score of > 90.

### NFR-2: Accuracy
- **NFR-2.1:** The Tech Stack extraction must achieve **95% accuracy** in identifying major frameworks and languages.

## 5. Interface Specifications

### API Endpoints
- `POST /api/portfolio/generate`: Triggers the generation job.
- `GET /api/portfolio/:id`: Retrieves the generated portfolio data.
- `POST /api/portfolio/:id/export`: Requests a PDF or Web export.

*Refer to [API Endpoints](../04-architecture/api-endpoints.md) for detailed schemas.*

## 6. Acceptance Criteria

- [ ] Generated portfolio correctly lists "React" and "TypeScript" for a frontend project.
- [ ] PDF export preserves the layout and styling of the selected template.
- [ ] User can successfully hide a "Toy Project" from the final portfolio.

## 7. Related Documents

- [F-004: Project Workspace](F-004-Project-Workspace.md)
- [System Architecture](../04-architecture/system-architecture.md)

