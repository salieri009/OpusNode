# P0: MVP Pages

**Directory:** TailCamp PRD - Page Design: P0 MVP  
**Last Updated:** 2025-11-28

---

## Overview

This directory contains all pages required for the Minimum Viable Product (MVP) launch. These pages form the core user journey: **Onboarding → Assessment → Matching → Group Formation**.

**Phase:** Phase 1 (Months 1-3)  
**Priority:** P0 (Must Have)  
**Status:** Core Value Validation

---

## Design Dependency Graph

```
Landing Page
    ↓
Sign Up → Email Verification
    ↓
Interest Selection → Goal Input
    ↓
Assessment Intro → AI Interview → Assessment Results
    ↓                                    ↓
Matching Queue → Match Found → Group Profile
    ↓
Solo Dashboard (Alternative path)
```

**Parallel Paths:**
- Login Page (independent entry point)
- Error Page (handles all error states)
- Terms & Privacy (legal requirement)

---

## Page List (15 Pages)

### A. Onboarding & Assessment Flow (8 Pages)

| # | Page | Document | Complexity | Dependencies |
|:--|:-----|:---------|:-----------|:-------------|
| 01 | Landing Page | [01-Landing-Page](01-Landing-Page.md) | 🟢 Low | None (Entry point) |
| 02 | Sign Up | [02-Sign-Up](02-Sign-Up.md) | 🟢 Low | Landing Page |
| 03 | Email Verification | [03-Email-Verification](03-Email-Verification.md) | 🟢 Low | Sign Up |
| 04 | Interest Selection | [04-Interest-Selection](04-Interest-Selection.md) | 🟢 Low | Email Verification |
| 05 | Goal Input | [05-Goal-Input](05-Goal-Input.md) | 🟢 Low | Interest Selection |
| 06 | Assessment Intro | [06-Assessment-Intro](06-Assessment-Intro.md) | 🟢 Low | Goal Input |
| 07 | AI Interview Interface | [07-AI-Interview-Interface](07-AI-Interview-Interface.md) | 🔥 High | Assessment Intro |
| 08 | Assessment Results | [08-Assessment-Results](08-Assessment-Results.md) | ⚡ Medium | AI Interview Interface |

**Feature Connection:** [F-001: AI Assessment](../../../03-features/F-001-AI-Assessment.md)

---

### B. Matching & Group Flow (3 Pages)

| # | Page | Document | Complexity | Dependencies |
|:--|:-----|:---------|:-----------|:-------------|
| 09 | Matching Queue | [09-Matching-Queue](09-Matching-Queue.md) | ⚡ Medium | Assessment Results |
| 10 | Match Found | [10-Match-Found](10-Match-Found.md) | 🟢 Low | Matching Queue |
| 11 | Group Profile | [11-Group-Profile](11-Group-Profile.md) | ⚡ Medium | Match Found |

**Feature Connection:** [F-002: Group Matching](../../../03-features/F-002-Group-Matching.md)

---

### C. Essential Pages (4 Pages)

| # | Page | Document | Complexity | Dependencies |
|:--|:-----|:---------|:-----------|:-------------|
| 16 | Login Page | [16-Login-Page](16-Login-Page.md) | 🟢 Low | None (Independent entry) |
| 18 | Solo Dashboard | [18-Solo-Dashboard](18-Solo-Dashboard.md) | ⚡ Medium | Assessment Results |
| 19 | Error Page | [19-Error-Page](19-Error-Page.md) | 🟢 Low | All pages (Error handler) |
| 20 | Terms & Privacy | [20-Terms-Privacy](20-Terms-Privacy.md) | 🟢 Low | Sign Up (Legal requirement) |

**Feature Connection:** [F-003: Learning Dashboard](../../../03-features/F-003-Learning-Dashboard.md) (Solo Dashboard)

---

## Development Order (Critical Path)

### Week 1-2: Foundation
1. **Landing Page** (01) - Entry point
2. **Sign Up** (02) - User registration
3. **Email Verification** (03) - Email confirmation
4. **Login Page** (16) - Authentication
5. **Error Page** (19) - Error handling
6. **Terms & Privacy** (20) - Legal compliance

### Week 3-4: Onboarding
7. **Interest Selection** (04) - User preferences
8. **Goal Input** (05) - Learning objectives
9. **Assessment Intro** (06) - Assessment preparation

### Week 5-6: Core Assessment (Critical)
10. **AI Interview Interface** (07) - **🔥 Highest Priority**
    - Requires: AI/LLM integration
    - Real-time chat + analysis panel
    - **Blocking:** Assessment Results, Matching Queue

11. **Assessment Results** (08) - Results visualization
    - Requires: AI Interview completion
    - Chart library integration

### Week 7-8: Matching & Group
12. **Matching Queue** (09) - Real-time matching
    - Requires: Assessment Results
    - WebSocket integration

13. **Match Found** (10) - Match celebration
    - Requires: Matching Queue completion

14. **Group Profile** (11) - Team dashboard
    - Requires: Match Found
    - Team management features

### Week 9-10: Solo Path
15. **Solo Dashboard** (18) - Individual learning
    - Requires: Assessment Results
    - Alternative to group matching
    - Curriculum visualization

---

## Design Dependencies

### Component Dependencies
- **Form Components:** Sign Up, Login, Goal Input, Interest Selection
- **Chat Interface:** AI Interview Interface (reusable for future chat features)
- **Chart Library:** Assessment Results (reusable for analytics)
- **Real-time Updates:** Matching Queue (WebSocket pattern for future features)

### Design System Dependencies
- **Color System:** All pages (consistent brand colors)
- **Typography:** All pages (consistent font hierarchy)
- **Button Styles:** All pages (primary, secondary, ghost)
- **Modal Patterns:** Email Verification, Assessment Intro, Error Page

---

## Integration Points

### Backend APIs Required
- **Auth Service:** Sign Up, Login, Email Verification
- **Assessment Service:** AI Interview Interface, Assessment Results
- **Matching Service:** Matching Queue, Match Found
- **Group Service:** Group Profile

### Third-party Integrations
- **Email Service:** Email Verification (SendGrid, AWS SES)
- **AI/LLM:** AI Interview Interface (OpenAI, Anthropic)
- **WebSocket:** Matching Queue (real-time updates)
- **Chart Library:** Assessment Results (Chart.js, Recharts)

---

## Acceptance Criteria (MVP)

### Must Have
- [ ] Complete onboarding flow (01-08) functional
- [ ] AI Interview Interface working with real-time analysis
- [ ] Matching algorithm produces groups
- [ ] Group Profile displays team information
- [ ] Solo Dashboard shows curriculum (if user skips matching)
- [ ] All error states handled gracefully
- [ ] Legal pages (Terms & Privacy) accessible

### Success Metrics
- 70% of users complete assessment
- 80% match success rate
- 40% Week 1 retention

---

## Related Documents

- [Development Roadmap](../../../06-roadmap/01-Development-Roadmap.md) - Phase 1 timeline
- [Features Overview](../../../03-features/README.md) - Feature priorities
- [UX/UI Principles](../../01-UX-UI-Principles.md) - Design system
- [User Journey Flows](../../02-User-Journey-Flows.md) - Flow context

---

**Next Phase:** [P1: Post-MVP Pages](../P1-Post-MVP/README.md)

