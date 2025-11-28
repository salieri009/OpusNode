# 06. Assessment Introduction

**Document:** TailCamp PRD - Page Design: Assessment Introduction  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Assessment Introduction page prepares users for the AI interview by explaining the process, duration, and privacy considerations. It serves as a confidence-building step before the actual assessment.

**Page Type:** Authenticated  
**Complexity:** 🟢 Low  
**Priority:** P0 (MVP)

**Related Documents:**
- [02-User-Journey-Flows](../../02-User-Journey-Flows.md) - Section 3.1.6
- **[F-001: AI Assessment](../../../03-features/F-001-AI-Assessment.md)** - Feature: Assessment introduction and preparation

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│                                         │
│         🤖 AI Assessment                │
│                                         │
│  I'll ask you 5-7 questions to         │
│  understand your current skills.        │
│                                         │
│  ⏱️ Takes about 10 minutes              │
│  🔒 Conversations are encrypted         │
│  📊 Results are private to you          │
│                                         │
│  What to expect:                        │
│  • Technical knowledge questions        │
│  • Experience-based questions           │
│  • Real-time skill analysis             │
│                                         │
│  [Begin Interview]                      │
│                                         │
│  [Skip for now] (secondary, ghost)      │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. Content Sections

### 3.1 Header
- **Icon:** AI/Robot emoji or icon
- **Title:** "AI Assessment"

### 3.2 Main Description
- **Text:** "I'll ask you 5-7 questions to understand your current skills."
- **Purpose:** Set expectations about question count

### 3.3 Key Information
- **Duration:** "⏱️ Takes about 10 minutes"
- **Privacy:** "🔒 Conversations are encrypted"
- **Confidentiality:** "📊 Results are private to you"

### 3.4 What to Expect
- **Bullet Points:**
  - Technical knowledge questions
  - Experience-based questions
  - Real-time skill analysis

### 3.5 Privacy Note (Expandable)
- **Default:** Collapsed
- **Content:** Explains data usage, encryption, storage
- **Link:** "Learn more about privacy"

---

## 4. Interactions

### 4.1 Primary Action
- **"Begin Interview" Button:** 
  - Navigate to AI Interview Interface
  - Shows loading state: "Starting interview..."

### 4.2 Secondary Action
- **"Skip for now" Button:**
  - Opens confirmation modal
  - Modal: "You can always take the assessment later. Continue without assessment?"
  - Options: [Cancel] [Continue without Assessment]

### 4.3 Privacy Expansion
- **"Learn more about privacy" Link:**
  - Expands privacy details section
  - Explains: Data usage, encryption, storage, GDPR compliance

---

## 5. States

### 5.1 Default
- All information visible
- Primary CTA prominent
- Privacy section collapsed

### 5.2 Loading (After Click)
- Button shows spinner
- Button text: "Starting interview..."
- Button disabled

### 5.3 Privacy Expanded
- Privacy details section visible
- "Learn more" link changes to "Show less"

### 5.4 Skip Confirmation
- Modal overlay appears
- Backdrop blur
- Confirmation message and buttons

---

## 6. Design Specifications

### 6.1 Components Used
- **Hero Section:** Centered content with icon
- **Information Cards:** Icon + text for key points
- **Button:** Primary (Begin Interview), Secondary Ghost (Skip)
- **Modal:** Confirmation dialog for skip action
- **Expandable Section:** Privacy details

### 6.2 Visual Hierarchy
- **Primary CTA:** Large, prominent button
- **Secondary CTA:** Smaller, less prominent, ghost style
- **Information:** Clear, scannable bullet points

---

## 7. Accessibility

- **Keyboard Navigation:** Tab to buttons, Enter to activate
- **Screen Reader:** "AI Assessment introduction. Takes about 10 minutes. Conversations are encrypted."
- **Focus Indicators:** 2px blue outline on interactive elements

---

## 8. Related Pages

- **Previous:** [05-Goal-Input](05-Goal-Input.md) - After goal input
- **Next:** [07-AI-Interview-Interface](07-AI-Interview-Interface.md) - User clicks "Begin Interview"
- **Alternative:** [18-Solo-Dashboard](18-Solo-Dashboard.md) - User clicks "Skip for now"

---

## 9. Acceptance Criteria

- [ ] All information is clearly displayed
- [ ] "Begin Interview" button navigates correctly
- [ ] "Skip for now" shows confirmation modal
- [ ] Privacy section expands/collapses correctly
- [ ] Loading state works on button click
- [ ] Page is fully keyboard accessible

---

**Next Step:** Review [02-User-Journey-Flows](../02-User-Journey-Flows.md) Section 3.1.6 for detailed flow context.

