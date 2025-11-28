# 14. Project Workspace

**Document:** TailCamp PRD - Page Design: Project Workspace  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Project Workspace is the most complex page, combining Kanban board, real-time chat, file sharing, and AI Coach in a three-column layout. It serves as the central collaboration hub for team projects.

**Page Type:** Authenticated (Group members only)  
**Complexity:** 🔥 High  
**Priority:** P0 (MVP)

**Related Documents:**
- [02-User-Journey-Flows](../../02-User-Journey-Flows.md) - Section 3.3.3
- **[F-004: Project Workspace](../../../03-features/F-004-Project-Workspace.md)** - **Core Feature:** Kanban board, GitHub integration, file sharing, AI Coach, activity aggregation (Section 5.1, 5.2)

---

## 2. Page Structure

### 2.1 Layout (Desktop)

```
┌─────────────────────────────────────────────────────────┐
│  [← Back]  E-commerce API  [Settings]  [Members 👥]     │
├──────────┬──────────────────────────────┬────────────────┤
│          │                              │                │
│ Left     │  Center Canvas              │  Right         │
│ Sidebar  │  (Kanban Board)             │  Sidebar       │
│ (20%)    │  (60%)                      │  (20%)         │
│          │                              │                │
│ Project  │  ┌──────┐ ┌──────┐ ┌──────┐│  AI Coach      │
│ Overview │  │ To Do│ │In Pro│ │ Done ││  ┌──────────┐  │
│          │  │      │ │gress │ │      ││  │💬 Need   │  │
│ Tech:    │  │[Card]│ │[Card]│ │[Card]││  │help with │  │
│ • Node   │  │[Card]│ │[Card]│ │[Card]││  │auth?     │  │
│ • PG     │  │      │ │      │ │      ││  └──────────┘  │
│          │  └──────┘ └──────┘ └──────┘│                │
│ Progress │                              │  Team Chat     │
│ ████░░░░ │  [Drag cards between columns]│  ┌──────────┐  │
│ 40%      │                              │  │💬 Alex:  │  │
│          │                              │  │"PR ready"│  │
│ GitHub   │                              │  │          │  │
│ [Link]   │                              │  │[Type...] │  │
│          │                              │  └──────────┘  │
│          │                              │                │
│          │                              │  File Sharing  │
│          │                              │  ┌──────────┐  │
│          │                              │  │📄 design │  │
│          │                              │  │📄 schema │  │
│          │                              │  │[Upload]  │  │
│          │                              │  └──────────┘  │
└──────────┴──────────────────────────────┴────────────────┘
```

---

## 3. Left Sidebar (20%)

### 3.1 Project Overview
- Project name, description
- Tech stack badges
- GitHub repo link
- Progress bar (0-100%)

### 3.2 Quick Actions
- View project settings
- View team members
- Project statistics

---

## 4. Center Canvas (60%) - Kanban Board

### 4.1 Columns
- **To Do:** Unassigned tasks
- **In Progress:** Active tasks
- **Review:** Tasks pending review
- **Done:** Completed tasks

### 4.2 Task Cards
- **Content:** Title, assignee, priority, due date
- **Drag & Drop:** Move between columns
- **Click:** Opens task detail modal
- **Quick Actions:** Hover shows assign, set due date, delete

---

## 5. Right Sidebar (20%)

### 5.1 AI Coach Widget
- **Context-Aware:** Analyzes project state
- **Suggestions:** "Need help with authentication? [Get help]"
- **Click:** Opens AI chat interface

### 5.2 Team Chat
- **Real-time:** WebSocket-based
- **Typing Indicators:** "Alex is typing..."
- **Mentions:** @username notifications
- **File Sharing:** Drag & drop or click to upload

### 5.3 File Sharing Panel
- **Upload:** Drag & drop or click
- **List:** Recent files with download
- **Preview:** Click to preview

---

## 6. Mobile Adaptations

### 6.1 Layout
- **Desktop:** Three-column layout
- **Mobile:** Tab-based navigation (Kanban, Chat, Files)

### 6.2 Interactions
- **Swipe Gestures:** Swipe left on task card → Quick actions
- **Tab Bar:** Switch between Kanban, Chat, Files

---

## 7. Real-time Features

### 7.1 WebSocket Integration
- **Task Updates:** Drag & drop syncs instantly
- **Chat Messages:** Instant delivery
- **File Uploads:** Progress indicator

### 7.2 States
- **Loading:** Skeleton screens
- **Offline:** "Reconnecting..." banner
- **Error:** Red error message, retry button

---

## 8. Related Pages

- **Previous:** [13-Project-Voting](13-Project-Voting.md) - After project selected
- **Next:** [15-Portfolio-Generator](15-Portfolio-Generator.md) - After project completion

---

## 9. Acceptance Criteria

- [ ] Kanban board works with drag & drop
- [ ] Real-time chat functions correctly
- [ ] File sharing works
- [ ] AI Coach provides relevant suggestions
- [ ] All updates sync in real-time
- [ ] Mobile layout is responsive

---

**Next Step:** Review [02-User-Journey-Flows](../02-User-Journey-Flows.md) Section 3.3.3 for detailed flow context.

