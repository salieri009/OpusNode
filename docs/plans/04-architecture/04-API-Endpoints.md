# API Endpoints

**Document:** TailCamp PRD - API Endpoints  
**Version:** 1.2  
**Last Updated:** 2025-11-23

---

## 1. Overview

This document specifies the REST API and GraphQL endpoints for the TailCamp platform. It serves as the contract between the Frontend and Backend teams.

**Related Documents:**
- [01-System-Architecture](01-System-Architecture.md)
- [03-Database-Schema](03-Database-Schema.md)

---

## 2. Authentication & User Management

### POST /api/auth/register
Registers a new user.

**Request:**
```json
{
  "email": "user@example.com",
  "name": "John Doe",
  "password": "password123"
}
```

**Response:**
```json
{
  "user": {
    "id": "uuid",
    "email": "user@example.com",
    "name": "John Doe",
    "email_verified": false
  },
  "token": "jwt_token"
}
```

### POST /api/auth/verify-email
Verifies the user's email address.

**Request:**
```json
{
  "token": "verification_token"
}
```

**Response:**
```json
{
  "message": "Email verified successfully"
}
```

### POST /api/auth/resend-verification
Resends the email verification link.

**Request:**
```json
{
  "email": "user@example.com"
}
```

**Response:**
```json
{
  "message": "Verification email sent"
}
```

### POST /api/auth/login
Authenticates a user.

**Request:**
```json
{
  "email": "user@example.com",
  "password": "password123"
}
```

**Response:**
```json
{
  "user": {
    "id": "uuid",
    "email": "user@example.com",
    "name": "John Doe"
  },
  "token": "jwt_token"
}
```

### POST /api/auth/refresh
Refreshes an expired access token.

**Headers:**
```
Authorization: Bearer <refresh_token>
```

**Response:**
```json
{
  "token": "new_jwt_token"
}
```

### GET /api/users/me
Retrieves the current user's profile.

**Response:**
```json
{
  "id": "uuid",
  "email": "user@example.com",
  "name": "John Doe",
  "interests": ["backend", "system_design"],
  "bio": "Backend enthusiast",
  "avatar_url": "https://..."
}
```

### PUT /api/users/me
Updates the current user's profile.

**Request:**
```json
{
  "name": "John Doe Updated",
  "bio": "New bio",
  "avatar_url": "https://..."
}
```

**Response:**
```json
{
  "id": "uuid",
  "name": "John Doe Updated",
  "bio": "New bio"
}
```

### PUT /api/users/interests
Updates the user's selected interests (Onboarding).

**Request:**
```json
{
  "interests": ["backend", "system_design", "cloud"]
}
```

**Response:**
```json
{
  "message": "Interests updated successfully",
  "interests": ["backend", "system_design", "cloud"]
}
```

---

## 3. Assessment [F-001]

### POST /api/assessment/start
Initiates a new assessment session.

**Headers:**
```
Authorization: Bearer <token>
```

**Response:**
```json
{
  "session_id": "uuid",
  "question": {
    "id": "q1",
    "text": "What is your experience with backend development?",
    "type": "open-ended"
  }
}
```

### POST /api/assessment/answer
Submits an answer to a question.

**Request:**
```json
{
  "session_id": "uuid",
  "question_id": "q1",
  "answer": "I have 2 years of experience..."
}
```

**Response:**
```json
{
  "next_question": {
    "id": "q2",
    "text": "...",
    "type": "multiple-choice"
  },
  "progress": 0.3
}
```

### GET /api/assessment/result/:id
Retrieves the results of a completed assessment.

**Response:**
```json
{
  "user_id": "uuid",
  "assessment_date": "2024-12-19T00:00:00Z",
  "scores": {
    "backend": 0.7,
    "frontend": 0.2
  },
  "level": "intermediate",
  "recommended_paths": ["backend_focused"]
}
```

---

## 4. Matching [F-002]

### POST /api/matching/join-queue
Adds the user to the matching queue.

**Request:**
```json
{
  "goals": ["backend", "api_design"],
  "preferred_group_size": 4
}
```

**Response:**
```json
{
  "queue_position": 5,
  "estimated_wait_time": "2 hours"
}
```

### GET /api/matching/status
Checks the current status of the user in the queue.

**Response:**
```json
{
  "status": "waiting",
  "queue_position": 3,
  "estimated_wait_time": "1 hour"
}
```

**Status Values:**
- `waiting`: In queue.
- `matching`: Algorithm processing.
- `matched`: Group formed.
- `failed`: Timeout or error.

### POST /api/matching/leave-queue
### POST /api/projects/:id/tasks
Adds a task to the project board.

**Request:**
```json
{
  "title": "Implement authentication",
  "description": "...",
  "assignee_id": "uuid",
  "priority": "high"
}
```

### POST /api/projects/:id/vote
Casts a vote for a project proposal (P1 Feature).

**Request:**
```json
{
  "vote_type": "upvote" 
}
```

**Response:**
```json
{
  "project_id": "uuid",
  "total_votes": 15,
  "user_vote": "upvote"
}
```5. Groups & Projects [F-004]

### GET /api/groups/:id
Retrieves group details.

**Response:**
```json
{
  "id": "uuid",
  "name": "Backend Learners",
  "status": "active",
  "members": [
    {
      "id": "uuid",
      "name": "John Doe",
      "role": "leader"
    }
  ]
}
```

### POST /api/projects
Creates a new project for a group.

**Request:**
```json
{
  "group_id": "uuid",
  "name": "E-commerce API",
  "description": "RESTful API for e-commerce",
  "tech_stack": ["Node.js", "PostgreSQL"]
}
```

**Response:**
```json
{
  "id": "uuid",
  "name": "E-commerce API",
  "status": "planning"
}
```

### POST /api/projects/:id/tasks
Adds a task to the project board.

**Request:**
```json
{
  "title": "Implement authentication",
  "description": "...",
  "assignee_id": "uuid",
  "priority": "high"
}
```

---

## 6. Curriculum [F-005]

### GET /api/curriculum/:userId
Retrieves the personalized curriculum.

**Response:**
```json
{
  "roadmap": {
    "weeks": [
      {
        "week": 1,
        "goals": ["Learn basics"],
        "tasks": [...]
      }
    ]
  },
  "current_week": 1
}
```

### PUT /api/curriculum/:userId/progress
Updates the progress of a curriculum item.

**Request:**
```json
{
  "week": 1,
  "completed_tasks": ["task1", "task2"]
}
```

---

## 7. Portfolio [F-006]

### POST /api/portfolio/generate
Triggers portfolio generation.

**Request:**
```json
{
  "project_ids": ["uuid1", "uuid2"],
  "template": "minimal"
}
```

### POST /api/portfolio/:id/export
Exports the portfolio to a specific format.

**Request:**
```json
{
  "format": "pdf"
}
```

---

## 8. Error Handling

### Error Response Format
```json
{
  "error": {
    "code": "ERROR_CODE",
    "message": "Error message",
    "details": {}
  }
}
```

### Common Error Codes
- `400`: Bad Request
- `401`: Unauthorized
- `403`: Forbidden
- `404`: Not Found
- `500`: Internal Server Error

---

## 9. Rate Limiting

- **Authentication**: 5 requests/minute
- **Assessment**: 10 requests/minute
- **Matching**: 3 requests/hour
- **General API**: 100 requests/minute

---

**Next Step:** Review [Success Metrics & KPIs](../05-metrics/success-metrics.md).

