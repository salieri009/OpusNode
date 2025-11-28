# 18. Solo Dashboard

**Document:** TailCamp PRD - Page Design: Solo Dashboard  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Solo Dashboard is the home screen for users who choose not to join a group or are waiting for a match. It displays personalized curriculum, progress tracking, and learning resources.

**Page Type:** Authenticated  
**Complexity:** ⚡ Medium  
**Priority:** P0 (MVP)

**Related Documents:**
- **[F-003: Learning Dashboard](../../../03-features/F-003-Learning-Dashboard.md)** - **Core Feature:** Personal roadmap visualization, progress tracking, AI task assistant (FR-1, FR-2, FR-3)
- **[F-005: Curriculum Generator](../../../03-features/F-005-Curriculum-Generator.md)** - **Feature:** Personalized curriculum generation, adaptive learning paths

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│  [Logo]              [Profile] [Settings]│
├─────────────────────────────────────────┤
│                                         │
│  Welcome back, [Name]!                  │
│                                         │
│  ┌───────────────────────────────────┐ │
│  │ Your Learning Roadmap             │ │
│  │ [DAG Visualization]                │ │
│  └───────────────────────────────────┘ │
│                                         │
│  Current Week's Tasks:                  │
│  ☐ Learn REST API basics               │
│  ☑ Complete Node.js tutorial           │
│  ☐ Build a simple API                  │
│                                         │
│  Progress: ████████░░ 80%              │
│                                         │
│  💡 AI Assistant:                      │
│  "Your next task: Build a simple API"  │
│                                         │
│  [Join a Team] [Continue Learning]     │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. Content Sections

### 3.1 Learning Roadmap
- **DAG Visualization:** Prerequisite relationships
- **Current Week:** Highlighted tasks
- **Progress:** Overall completion percentage

### 3.2 Current Week's Tasks
- **Checklist:** Tasks for the week
- **Status:** Completed/incomplete
- **Click:** Mark as complete

### 3.3 AI Assistant Widget
- **Suggestions:** "Next Best Action"
- **Click:** Opens AI chat for help

### 3.4 Quick Actions
- **Join a Team:** Navigate to matching
- **Continue Learning:** View full curriculum

---

## 4. Related Pages

- **From:** [08-Assessment-Results](08-Assessment-Results.md) - User clicked "Explore Solo"
- **To:** [09-Matching-Queue](09-Matching-Queue.md) - User clicks "Join a Team"

---

## 5. Acceptance Criteria

- [ ] Roadmap displays correctly
- [ ] Tasks can be marked complete
- [ ] Progress updates correctly
- [ ] AI Assistant provides suggestions
- [ ] Mobile layout is responsive

---

**Next Step:** Review [F-003: Learning Dashboard](../../03-features/F-003-Learning-Dashboard.md) for feature requirements.

