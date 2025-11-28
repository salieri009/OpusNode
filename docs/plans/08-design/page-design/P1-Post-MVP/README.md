# P1: Post-MVP Pages

**Directory:** TailCamp PRD - Page Design: P1 Post-MVP  
**Last Updated:** 2025-11-28

---

## Overview

This directory contains pages for Phase 2 (Months 4-6) that enhance collaboration and enable project-based learning. These pages build upon the MVP foundation to provide full project lifecycle management.

**Phase:** Phase 2 (Months 4-6)  
**Priority:** P1 (Should Have)  
**Status:** Collaboration & Engagement

---

## Design Dependency Graph

```
Group Profile (P0)
    ↓
Project Proposal → Project Voting
    ↓
Project Workspace
    ↓
Portfolio Generator
```

**Independent:**
- User Profile / Settings (can be developed in parallel)

---

## Page List (5 Pages)

### A. Project & Portfolio Flow (4 Pages)

| # | Page | Document | Complexity | Dependencies |
|:--|:-----|:---------|:-----------|:-------------|
| 12 | Project Proposal | [12-Project-Proposal](12-Project-Proposal.md) | 🟢 Low | Group Profile (P0) |
| 13 | Project Voting | [13-Project-Voting](13-Project-Voting.md) | ⚡ Medium | Project Proposal |
| 14 | Project Workspace | [14-Project-Workspace](14-Project-Workspace.md) | 🔥 High | Project Voting |
| 15 | Portfolio Generator | [15-Portfolio-Generator](15-Portfolio-Generator.md) | ⚡ Medium | Project Workspace |

**Feature Connection:** 
- [F-004: Project Workspace](../../../03-features/F-004-Project-Workspace.md) (12-14)
- [F-006: Portfolio Generator](../../../03-features/F-006-Portfolio-Generator.md) (15)

---

### B. User Management (1 Page)

| # | Page | Document | Complexity | Dependencies |
|:--|:-----|:---------|:-----------|:-------------|
| 17 | User Profile / Settings | [17-User-Profile-Settings](17-User-Profile-Settings.md) | ⚡ Medium | None (Independent) |

**Feature Connection:** User management (independent feature)

---

## Development Order

### Month 4: Project Planning
1. **Project Proposal** (12) - Project idea submission
   - Requires: Group Profile (P0) completed
   - Simple form, AI suggestions

2. **Project Voting** (13) - Democratic project selection
   - Requires: Project Proposal
   - Real-time voting, comments

### Month 5: Collaboration Hub
3. **Project Workspace** (14) - **🔥 Highest Priority in P1**
   - Requires: Project Voting completion
   - Most complex page: Kanban + Chat + Files
   - Integration with GitHub, Slack (Phase 2 scope)

### Month 6: Portfolio & Polish
4. **Portfolio Generator** (15) - Project showcase
   - Requires: Project Workspace with completed projects
   - Template selection, PDF export

5. **User Profile / Settings** (17) - Account management
   - Can be developed in parallel
   - Profile updates, privacy settings

---

## Design Dependencies

### From P0 Pages
- **Group Profile** (P0) → Project Proposal (entry point)
- **Design System** (P0) → All P1 pages (consistent styling)
- **Chat Interface** (P0 AI Interview) → Project Workspace Chat (reusable pattern)
- **Real-time Updates** (P0 Matching Queue) → Project Voting (WebSocket pattern)

### New Components Required
- **Kanban Board:** Project Workspace (drag & drop)
- **File Upload/Sharing:** Project Workspace
- **Portfolio Templates:** Portfolio Generator
- **Calendar Integration:** Project Workspace (meeting scheduling)

---

## Integration Points

### Backend APIs Required
- **Project Service:** Project Proposal, Project Voting
- **Workspace Service:** Project Workspace (Kanban, Chat, Files)
- **Portfolio Service:** Portfolio Generator
- **User Service:** User Profile / Settings

### Third-party Integrations
- **GitHub API:** Project Workspace (code integration)
- **Slack API:** Project Workspace (notifications)
- **File Storage:** Project Workspace (S3, Cloudinary)
- **PDF Generation:** Portfolio Generator (jsPDF, Puppeteer)

---

## Feature Scope (Phase 2)

### Project Workspace (F-004 Phase 2)
- **Integration Only:** Auto-setup for Slack/GitHub
- **Activity Feed:** Webhooks implementation
- **Native Features:** Deferred to Phase 3

### Portfolio Generator (F-006)
- **Auto-generation:** From project data
- **Templates:** 3 template options
- **Export:** PDF and Web formats

---

## Acceptance Criteria (P1)

### Must Have
- [ ] Teams can propose and vote on projects
- [ ] Project Workspace integrates with GitHub/Slack
- [ ] Kanban board functional with drag & drop
- [ ] Real-time chat works in workspace
- [ ] Portfolio can be generated from completed projects
- [ ] User can update profile and settings

### Success Metrics
- 60% of groups start a project
- 50% project completion rate
- 30% portfolio generation rate

---

## Related Documents

- [Development Roadmap](../../../06-roadmap/01-Development-Roadmap.md) - Phase 2 timeline
- [Features Overview](../../../03-features/README.md) - Feature priorities
- [P0 MVP Pages](../P0-MVP/README.md) - Prerequisite pages
- [UX/UI Principles](../../01-UX-UI-Principles.md) - Design system

---

**Previous Phase:** [P0: MVP Pages](../P0-MVP/README.md)

