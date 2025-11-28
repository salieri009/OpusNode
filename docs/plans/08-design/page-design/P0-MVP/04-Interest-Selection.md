# 04. Interest Selection

**Document:** TailCamp PRD - Page Design: Interest Selection  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Interest Selection page allows users to choose 1-3 technology areas they're interested in learning. This selection influences the assessment questions and curriculum recommendations.

**Page Type:** Authenticated (Post-email verification)  
**Complexity:** 🟢 Low  
**Priority:** P0 (MVP)

**Related Documents:**
- [02-User-Journey-Flows](../../02-User-Journey-Flows.md) - Section 3.1.4
- [01-UX-UI-Principles](../../01-UX-UI-Principles.md) - Section 2.1 (Interest Selection)
- **[F-001: AI Assessment](../../../03-features/F-001-AI-Assessment.md)** - Feature: Interest selection influences assessment questions

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│  [← Back]                               │
│                                         │
│  What are you interested in?           │
│  Select 1-3 areas (required)            │
│                                         │
│  ┌──────┐ ┌──────┐ ┌──────┐           │
│  │ 🔵   │ │ ⚪   │ │ ⚪   │           │
│  │Backend│ │Frontend│ │ AI/ML │           │
│  └──────┘ └──────┘ └──────┘           │
│                                         │
│  ┌──────┐ ┌──────┐ ┌──────┐           │
│  │ ⚪   │ │ ⚪   │ │ ⚪   │           │
│  │Mobile │ │DevOps│ │Data  │           │
│  └──────┘ └──────┘ └──────┘           │
│                                         │
│  Selected: Backend (1/3)                │
│                                         │
│  [Continue to Goals] (disabled)        │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. Interest Options

### 3.1 Available Interests
- Backend Development
- Frontend Development
- AI/ML
- Mobile Development
- DevOps
- Data Science
- Full-Stack Development
- Cloud Computing

### 3.2 Selection Rules
- **Minimum:** 1 selection required
- **Maximum:** 3 selections allowed
- **Visual Feedback:** Selected cards show blue border, checkmark icon

---

## 4. Interactions

### 4.1 Card Selection
- **Click/Tap:** Toggle selection
- **Animation:** 
  - Scale: 1.05x on selection
  - Border color transition: 200ms
  - Checkmark fade-in: 200ms

### 4.2 Selection Counter
- **Display:** "Selected: X (1-3)"
- **Updates:** Real-time as user selects/deselects
- **Color:** Blue when valid (1-3), red when invalid (0 or >3)

### 4.3 Continue Button
- **State:** Disabled until 1+ selected
- **Enabled:** When 1-3 selections made
- **Animation:** Smooth enable/disable transition

---

## 5. States

### 5.1 Default
- No selections, button disabled
- All cards in unselected state (white border)

### 5.2 Selecting
- Cards toggle on click
- Counter updates in real-time
- Button state changes based on selection count

### 5.3 Valid (1-3 Selected)
- Button enabled
- Counter shows blue "Selected: X (1-3)"
- Ready to proceed

### 5.4 Invalid (>3 Selected)
- Button disabled
- Counter shows red "Selected: X (max 3)"
- Error message: "Please select no more than 3 areas"

---

## 6. Mobile Adaptations

### 6.1 Layout
- **Desktop:** 3-column grid
- **Tablet:** 2-column grid
- **Mobile:** 2-column grid, larger touch targets (min 44x44px)

### 6.2 Interactions
- **Swipeable Carousel:** Optional for mobile (if many options)
- **Touch Feedback:** Haptic feedback on selection (if supported)

---

## 7. Design Specifications

### 7.1 Card Design
- **Unselected:** White background, gray border, no checkmark
- **Selected:** Blue border (#0a95ff), checkmark icon, subtle scale
- **Hover:** Slight elevation, cursor pointer

### 7.2 Components Used
- **Interest Cards:** Interactive cards with icon, title
- **Selection Counter:** Real-time counter display
- **Button:** Primary CTA (Continue to Goals)
- **Back Button:** Navigate to previous step

---

## 8. Accessibility

- **Keyboard Navigation:** Tab through cards, Enter to select
- **Screen Reader:** "Backend Development, not selected. Press Enter to select."
- **Focus Indicators:** 2px blue outline on focused card
- **ARIA Labels:** "Interest selection: Backend Development"

---

## 9. Related Pages

- **Previous:** [03-Email-Verification](03-Email-Verification.md) - After email verified
- **Next:** [05-Goal-Input](05-Goal-Input.md) - User clicks "Continue to Goals"
- **Back:** [03-Email-Verification](03-Email-Verification.md) - User clicks back button

---

## 10. Acceptance Criteria

- [ ] Users can select 1-3 interests
- [ ] Selection counter updates correctly
- [ ] Button enables/disables based on selection count
- [ ] Card animations are smooth
- [ ] Mobile layout is responsive
- [ ] Keyboard navigation works correctly

---

**Next Step:** Review [02-User-Journey-Flows](../02-User-Journey-Flows.md) Section 3.1.4 for detailed flow context.

