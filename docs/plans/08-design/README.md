# UX/UI Design & Brand

**Directory:** TailCamp PRD - Design  
**Last Updated:** 2025-11-28

---

## Page Design Specifications

Detailed page-by-page design specifications are available in the [Page Design](page-design/) directory, covering all 20 screens:

- **Onboarding & Assessment (8 pages):** Landing, Sign Up, Email Verification, Interest Selection, Goal Input, Assessment Intro, AI Interview, Results
- **Matching & Group (3 pages):** Matching Queue, Match Found, Group Profile
- **Project & Portfolio (4 pages):** Project Proposal, Voting, Workspace, Portfolio Generator
- **Essential Pages (5 pages):** Login, User Profile/Settings, Solo Dashboard, Error Page, Terms & Privacy

**See:** [Page Design Directory](page-design/README.md) for complete list and complexity classification.

---

## Overview

This directory contains user experience design principles, detailed user flows, design system specifications, and accessibility guidelines for TailCamp.

## Documents

| Document | Description | Audience |
|:---------|:------------|:---------|
| **[01-UX-UI-Principles](01-UX-UI-Principles.md)** | Design philosophy, basic user flows with mermaid diagrams, design system, and accessibility standards. | Designers, Frontend Engineers |
| **[02-User-Journey-Flows](02-User-Journey-Flows.md)** | Comprehensive user journey maps and detailed screen-by-screen UX flows with interaction states, error handling, and edge cases. | Designers, Frontend Engineers, QA |
| **[03-Design-Features-Integration](03-Design-Features-Integration.md)** | Detailed mapping of how design documents connect to feature specifications, with rationale for design decisions. | All Stakeholders, PM, Designers, Engineers |
| **[Page Design](page-design/README.md)** | Detailed page-by-page design specifications for all 20 screens in the platform. | Designers, Frontend Engineers, QA |

## Design Philosophy

1.  **Clarity First:** Complex functionality made intuitive
2.  **Progressive Disclosure:** Reduce cognitive load by revealing information gradually
3.  **Delightful Moments:** Micro-animations that enhance UX without distraction
4.  **Accessibility:** WCAG 2.1 AA compliance for all users

## Key User Flows

### Flow 1: Onboarding → Assessment
Sign Up → Email Verification → Interest Selection → Goal Input → AI Interview → Results

**Goal:** <15 minutes to completed assessment

### Flow 2: Assessment → Matching → Group
Results → Join Queue → Waiting Screen (2-6 hrs) → Match Found → Group Profile → First Meeting

**Goal:** Build trust in algorithmic matching through transparency

### Flow 3: Group → Project → Portfolio
Dashboard → Propose Project → Vote → Workspace (Kanban board) → Complete → Generate Portfolio

**Goal:** Seamless transition from team to deliverable

## Design System

-   **Colors:** Primary Blue (#0a95ff), Secondary Green (#22c55e), Accent Orange (#f97316)
-   **Typography:** Inter (UI), JetBrains Mono (Code)
-   **Components:** Buttons, Cards, Modals, Input fields
-   **Responsive:** Mobile-first (<768px → 768-1024px → >1024px)

## Related Sections

-   [Features Overview](../03-features/) - Feature specifications that inform design
-   [Security & Privacy](../09-security/) - Accessibility and privacy by design

---

**Quick Links:**
- **[← Back to Main PRD](../README.md)**
- **[View UX/UI Principles →](01-UX-UI-Principles.md)**
- **[View User Journey Flows →](02-User-Journey-Flows.md)**
- **[View Design-Features Integration →](03-Design-Features-Integration.md)**
- **[View Page Design Specifications →](page-design/README.md)**
