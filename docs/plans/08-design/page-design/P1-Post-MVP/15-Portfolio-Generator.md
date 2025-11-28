# 15. Portfolio Generator

**Document:** TailCamp PRD - Page Design: Portfolio Generator  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Portfolio Generator allows users to select completed projects, choose a template, and generate a professional portfolio with auto-populated content from project data and GitHub commits.

**Page Type:** Authenticated  
**Complexity:** ⚡ Medium  
**Priority:** P1 (Post-MVP)

**Related Documents:**
- [02-User-Journey-Flows](../../02-User-Journey-Flows.md) - Section 3.3.4
- **[F-006: Portfolio Generator](../../../03-features/F-006-Portfolio-Generator.md)** - **Core Feature:** Automated content generation, template system, PDF/Web export (FR-1, FR-2, FR-3)

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│  [← Back]                               │
├─────────────────────────────────────────┤
│                                         │
│  Generate Your Portfolio                │
│                                         │
│  Select Projects:                       │
│  ☑ E-commerce API (Completed)          │
│  ☑ Task Management App (Completed)      │
│  ☐ Learning Dashboard (In Progress)    │
│                                         │
│  Choose Template:                       │
│  ┌──────┐ ┌──────┐ ┌──────┐          │
│  │Minimal│ │Professional│ │Creative│  │
│  │  ●   │ │      │ │      │          │
│  └──────┘ └──────┘ └──────┘          │
│                                         │
│  Preview:                               │
│  ┌───────────────────────────────────┐ │
│  │                                   │ │
│  │  [Live Preview of Portfolio]      │ │
│  │                                   │ │
│  └───────────────────────────────────┘ │
│                                         │
│  [Generate Portfolio]                   │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. Project Selection

### 3.1 Project List
- **Checkboxes:** Select multiple completed projects
- **Status:** Shows completion status
- **Filter:** Show only completed projects

### 3.2 Auto-populated Content
- Project name, description
- Tech stack (from project data)
- Contributions (from GitHub commits)
- Screenshots (user-uploaded)

---

## 4. Template Selection

### 4.1 Template Options
- **Minimal:** Clean, text-focused, single column
- **Professional:** Corporate style, two columns, formal
- **Creative:** Colorful, modern, interactive elements

### 4.2 Live Preview
- **Display:** Real-time preview of selected template
- **Update:** Changes as user selects different template
- **Scrollable:** Full portfolio preview

---

## 5. Generation Process

### 5.1 Steps
1. "Analyzing your projects... (1/3)"
2. "Generating content... (2/3)"
3. "Creating portfolio... (3/3)"
4. Success: "Portfolio ready! [View] [Export]"

### 5.2 Export Options
- **PDF:** High-resolution, print-ready
- **Web:** Hosted URL (username.tailcamp.io/portfolio)
- **Share:** Social media sharing buttons

---

## 6. Related Pages

- **Previous:** [14-Project-Workspace](14-Project-Workspace.md) - After project completion
- **Next:** Portfolio view/export page

---

## 7. Acceptance Criteria

- [ ] Project selection works correctly
- [ ] Template preview updates in real-time
- [ ] Generation process shows progress
- [ ] Export options work (PDF, Web)
- [ ] Auto-populated content is accurate

---

**Next Step:** Review [02-User-Journey-Flows](../02-User-Journey-Flows.md) Section 3.3.4 for detailed flow context.

