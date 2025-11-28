# 12. Project Proposal

**Document:** TailCamp PRD - Page Design: Project Proposal  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Project Proposal page allows team members to propose project ideas with details about tech stack, duration, and difficulty level. It includes AI suggestions for project ideas based on team interests.

**Page Type:** Authenticated (Group members only)  
**Complexity:** 🟢 Low  
**Priority:** P0 (MVP)

**Related Documents:**
- [02-User-Journey-Flows](../../02-User-Journey-Flows.md) - Section 3.3.1
- **[F-004: Project Workspace](../../../03-features/F-004-Project-Workspace.md)** - **Feature:** Project proposal submission, AI suggestions for project ideas (entry point for workspace)

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│  [← Back to Group]                      │
├─────────────────────────────────────────┤
│                                         │
│  Propose a Project                      │
│                                         │
│  Project Name:                          │
│  [_____________________________]        │
│                                         │
│  Description:                           │
│  ┌───────────────────────────────────┐ │
│  │                                   │ │
│  │  [Describe your project idea...] │ │
│  │                                   │ │
│  └───────────────────────────────────┘ │
│                                         │
│  Tech Stack (select multiple):          │
│  [Node.js] [React] [PostgreSQL] [+]    │
│                                         │
│  Estimated Duration:                    │
│  ○ 2 weeks  ○ 1 month  ● 2-3 months   │
│                                         │
│  Difficulty Level:                      │
│  ○ Beginner  ● Intermediate  ○ Advanced│
│                                         │
│  [Propose Project]                      │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. Form Fields

### 3.1 Project Name
- **Type:** Text input
- **Validation:** Required, 3-100 characters
- **Placeholder:** "E-commerce API"

### 3.2 Description
- **Type:** Textarea
- **Validation:** Required, 50-1000 characters
- **Placeholder:** "Describe your project idea..."
- **Character Counter:** Real-time (X/1000)

### 3.3 Tech Stack
- **Type:** Multi-select chips
- **Options:** Searchable dropdown
- **Display:** Selected technologies as chips
- **Add More:** "+" button to add more technologies

### 3.4 Estimated Duration
- **Type:** Radio buttons
- **Options:**
  - 2 weeks
  - 1 month
  - 2-3 months
  - 3+ months

### 3.5 Difficulty Level
- **Type:** Radio buttons with descriptions
- **Options:**
  - Beginner (with description)
  - Intermediate (with description)
  - Advanced (with description)

---

## 4. Interactions

### 4.1 AI Suggestions
- **"Need ideas?" Button:** Opens AI project generator
- **Input:** User can describe what they want to build
- **Output:** 3 project suggestions with descriptions
- **Example:** "I want to build something with React and Node.js"
- **Result:** 3 project ideas with tech stacks

### 4.2 Tech Stack Selection
- **Search:** Type to search technologies
- **Select:** Click to add to selection
- **Remove:** Click chip X to remove
- **Visual:** Selected chips highlighted

### 4.3 Form Validation
- **Real-time:** Validation as user types
- **Submit:** Button enabled when all fields valid
- **Error Messages:** Clear, actionable feedback

---

## 5. States

### 5.1 Default
- All fields empty
- Submit button disabled
- No suggestions shown

### 5.2 Filling Form
- Fields validate in real-time
- Submit button enables when valid
- Character counter updates

### 5.3 AI Suggestions Open
- Modal or expandable section
- AI generating suggestions (loading state)
- Suggestions displayed as cards

### 5.4 Submitting
- Loading spinner on submit button
- Fields disabled
- "Creating project proposal..." message

### 5.5 Success
- Success message
- Redirect to Project Voting page

---

## 6. Design Specifications

### 6.1 Components Used
- **Input Fields:** Text, Textarea
- **Multi-select:** Tech stack chips with search
- **Radio Buttons:** Duration and difficulty
- **Button:** Primary (Propose Project), Secondary (Need ideas?)
- **Modal:** AI suggestions modal

### 6.2 Visual Feedback
- **Valid:** Green checkmark, enabled button
- **Invalid:** Red border, error message, disabled button
- **Loading:** Spinner on submit

---

## 7. Accessibility

- **Keyboard Navigation:** Tab through all fields
- **Screen Reader:** "Project proposal form. Project name field."
- **Focus Indicators:** 2px blue outline
- **Error Announcements:** Screen reader announces errors

---

## 8. Related Pages

- **Previous:** [11-Group-Profile](11-Group-Profile.md) - User clicked "Start Project"
- **Next:** [13-Project-Voting](13-Project-Voting.md) - After proposal submitted
- **Back:** [11-Group-Profile](11-Group-Profile.md) - User clicks back

---

## 9. Acceptance Criteria

- [ ] All form fields validate correctly
- [ ] Tech stack multi-select works
- [ ] AI suggestions generate correctly
- [ ] Form submission works
- [ ] Error messages are clear
- [ ] Mobile layout is responsive
- [ ] Form is keyboard accessible

---

**Next Step:** Review [02-User-Journey-Flows](../02-User-Journey-Flows.md) Section 3.3.1 for detailed flow context.

