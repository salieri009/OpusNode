# 11. Group Profile

**Document:** TailCamp PRD - Page Design: Group Profile  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Group Profile page is the team dashboard where members can view team information, set up the first meeting, edit the group charter, and start their first project. It serves as the central hub for group activities.

**Page Type:** Authenticated (Group members only)  
**Complexity:** ⚡ Medium  
**Priority:** P0 (MVP)

**Related Documents:**
- [02-User-Journey-Flows](../../02-User-Journey-Flows.md) - Section 3.2.3
- **[F-002: Group Matching](../../../03-features/F-002-Group-Matching.md)** - **Core Feature:** Team dashboard, member profiles, group charter, first meeting setup
- [F-004: Project Workspace](../../../03-features/F-004-Project-Workspace.md) - Project connection (entry point)

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│  [← Back]              [Settings ⚙️]    │
├─────────────────────────────────────────┤
│                                         │
│  Backend Builders - Cohort 42           │
│  👥 4 members  |  🎯 Active            │
│                                         │
│  ┌───────────────────────────────────┐ │
│  │ Team Members                      │ │
│  │                                   │ │
│  │  [Card] [Card] [Card] [Card]     │ │
│  │  (Click to view profile)          │ │
│  └───────────────────────────────────┘ │
│                                         │
│  Shared Learning Goal:                  │
│  "Build a full-stack e-commerce app"   │
│                                         │
│  Suggested First Meeting:               │
│  📅 This Saturday, 2 PM                │
│  💬 Icebreaker: "What's your            │
│     favorite programming language?"    │
│                                         │
│  [Schedule First Meeting]               │
│  [Start Project]                        │
│                                         │
│  ┌───────────────────────────────────┐ │
│  │ Group Charter                     │ │
│  │                                   │ │
│  │  ✓ We commit to daily updates    │ │
│  │  ✓ We respect each other's time  │ │
│  │  ✓ We celebrate small wins       │ │
│  │                                   │ │
│  │  [Edit Charter]                  │ │
│  └───────────────────────────────────┘ │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. Content Sections

### 3.1 Header
- **Group Name:** "Backend Builders - Cohort 42"
- **Metadata:** Member count, status (Active/Inactive)
- **Actions:** Back button, Settings button

### 3.2 Team Members
- **Display:** Member cards in grid layout
- **Per Card:**
  - Avatar
  - Name
  - Top skills
  - Level (star rating)
- **Click:** Opens full profile modal

### 3.3 Shared Learning Goal
- **Display:** Prominent text display
- **Source:** From matching algorithm
- **Purpose:** Reinforce why group was formed

### 3.4 Suggested First Meeting
- **Date/Time:** "This Saturday, 2 PM"
- **Icebreaker:** AI-generated question
- **Action:** "Schedule First Meeting" button

### 3.5 Group Charter
- **Format:** Checklist of group norms
- **Default Items:** Pre-filled suggestions
- **Editable:** All members can suggest changes
- **Voting:** Changes require majority approval

---

## 4. Interactions

### 4.1 Member Card Click
- **Action:** Opens profile modal
- **Modal Content:**
  - Assessment results (if shared)
  - Previous projects
  - Availability
  - Contact info (if opted in)

### 4.2 Schedule First Meeting
- **Action:** Opens calendar picker
- **Time Suggestions:** Based on member availability
- **Meeting Link:** Auto-generates Zoom/Google Meet link
- **Integration:** Calendar API integration

### 4.3 Start Project
- **Action:** Navigate to Project Proposal page
- **Purpose:** Begin project planning

### 4.4 Edit Charter
- **Action:** Opens charter editor
- **Process:** Suggest changes, vote on updates
- **Approval:** Majority vote required

---

## 5. States

### 5.1 Default
- All sections visible
- Member cards interactive
- CTAs enabled

### 5.2 Profile Modal Open
- Modal overlay
- Full member profile displayed
- Backdrop blur

### 5.3 Calendar Picker Open
- Calendar widget displayed
- Time slots highlighted
- Meeting link generated

---

## 6. Design Specifications

### 6.1 Components Used
- **Member Cards:** Interactive profile cards
- **Modal:** Profile detail modal
- **Calendar Picker:** Meeting scheduling widget
- **Charter Editor:** Editable checklist
- **Buttons:** Primary (Schedule Meeting, Start Project), Secondary (Edit Charter)

### 6.2 Visual Hierarchy
- **Group Name:** Large, prominent
- **Members:** Clear grid layout
- **Shared Goal:** Highlighted section
- **CTAs:** Prominent buttons

---

## 7. Accessibility

- **Screen Reader:** "Group: Backend Builders. 4 members. Shared goal: Build a full-stack e-commerce app."
- **Keyboard Navigation:** Tab through cards, Enter to open profile
- **Focus Indicators:** Clear focus on interactive elements

---

## 8. Related Pages

- **Previous:** [10-Match-Found](10-Match-Found.md) - After match found
- **Next (Primary):** [12-Project-Proposal](12-Project-Proposal.md) - User clicks "Start Project"
- **Next (Secondary):** Calendar integration for meeting scheduling
- **Settings:** Group settings page (future)

---

## 9. Acceptance Criteria

- [ ] Group information displays correctly
- [ ] Member cards are clickable
- [ ] Profile modal opens correctly
- [ ] Calendar picker works for meeting scheduling
- [ ] Charter editor allows edits and voting
- [ ] CTAs navigate to correct pages
- [ ] Page is responsive on mobile

---

**Next Step:** Review [02-User-Journey-Flows](../02-User-Journey-Flows.md) Section 3.2.3 for detailed flow context.

