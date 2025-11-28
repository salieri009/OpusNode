# Page Design Specifications

**Directory:** TailCamp PRD - Page Design  
**Last Updated:** 2025-11-28

---

## Overview

This directory contains detailed page-by-page design specifications for all screens in the TailCamp platform. Each page document includes layout, interactions, states, and design rationale.

**Purpose:**
- Provide detailed specifications for frontend implementation
- Ensure design consistency across all pages
- Document interaction patterns and edge cases
- Support design reviews and QA testing

**Related Documents:**
- [01-UX-UI-Principles](../01-UX-UI-Principles.md) - Design philosophy and system
- [02-User-Journey-Flows](../02-User-Journey-Flows.md) - User flow context
- [03-Design-Features-Integration](../03-Design-Features-Integration.md) - Feature connections

---

## Development Phases

Pages are organized by development priority and phase, considering design dependencies and critical path.

### P0: MVP Pages (Phase 1 - Months 1-3)

**15 Pages** - Core value validation: Onboarding → Assessment → Matching → Group Formation

**See:** [P0-MVP Directory](P0-MVP/README.md) for complete list and dependencies.

**Key Pages:**
- Onboarding & Assessment Flow (8 pages): Landing → Sign Up → Email Verification → Interest → Goal → Assessment Intro → AI Interview → Results
- Matching & Group Flow (3 pages): Matching Queue → Match Found → Group Profile
- Essential Pages (4 pages): Login, Solo Dashboard, Error Page, Terms & Privacy

### P1: Post-MVP Pages (Phase 2 - Months 4-6)

**5 Pages** - Collaboration & engagement: Project lifecycle management

**See:** [P1-Post-MVP Directory](P1-Post-MVP/README.md) for complete list and dependencies.

**Key Pages:**
- Project & Portfolio Flow (4 pages): Project Proposal → Project Voting → Project Workspace → Portfolio Generator
- User Management (1 page): User Profile / Settings

---

## Complexity Classification

### 🔥 High Complexity
- **07-AI-Interview-Interface:** Real-time chat UI + live analysis graph integration
- **14-Project-Workspace:** Kanban (D&D), chat (Socket), file management in one screen

### ⚡ Medium Complexity
- **09-Matching-Queue:** Real-time status updates (WebSocket)
- **08-Assessment-Results:** Chart visualization library integration
- **13-Project-Voting:** Real-time vote counting and comments
- **15-Portfolio-Generator:** Template selection with live preview
- **17-User-Profile-Settings:** Multiple form sections with validation
- **18-Solo-Dashboard:** Curriculum visualization and progress tracking

### 🟢 Low Complexity
- **01-20 (Others):** Static forms, simple layouts, informational pages

---

## Design Dependencies

### Critical Path (P0)
```
Landing → Sign Up → Email Verification → Interest → Goal → Assessment Intro 
→ AI Interview → Assessment Results → Matching Queue → Match Found → Group Profile
```

**Alternative Path:**
```
Assessment Results → Solo Dashboard (if user skips matching)
```

### Post-MVP Path (P1)
```
Group Profile (P0) → Project Proposal → Project Voting → Project Workspace → Portfolio Generator
```

**See detailed dependency graphs in:**
- [P0-MVP README](P0-MVP/README.md) - MVP dependencies
- [P1-Post-MVP README](P1-Post-MVP/README.md) - Post-MVP dependencies

---

## Related Documents

- [02-User-Journey-Flows](../02-User-Journey-Flows.md) - Detailed flow context for each page
- [01-UX-UI-Principles](../01-UX-UI-Principles.md) - Design system and components
- [Features Overview](../../03-features/README.md) - Feature requirements

---

**Quick Links:**
- **[← Back to Design](../README.md)**
- **[P0: MVP Pages →](P0-MVP/README.md)** - Phase 1 pages (15 pages)
- **[P1: Post-MVP Pages →](P1-Post-MVP/README.md)** - Phase 2 pages (5 pages)
- **[View UX/UI Principles →](../01-UX-UI-Principles.md)**
- **[View User Journey Flows →](../02-User-Journey-Flows.md)**

