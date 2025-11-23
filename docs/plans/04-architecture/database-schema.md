# Database Schema

**Document:** TailCamp PRD - Database Schema  
**Version:** 1.2  
**Last Updated:** 2025-11-23

---

## 1. Overview

This document defines the database schema for the TailCamp platform, using PostgreSQL as the primary relational database. It details the core tables, relationships, and indexing strategies to ensure performance and data integrity.

**Related Documents:**
- [System Architecture](system-architecture.md)
- [Technology Stack](technology-stack.md)

---

## 2. Core Tables

### 2.1 Users Table
Stores fundamental user information and authentication credentials.

```sql
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) UNIQUE NOT NULL,
  name VARCHAR(100) NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  role VARCHAR(50) DEFAULT 'user', -- 'user', 'admin', 'moderator'
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_role ON users(role);
```

**Relationships:**
-   Referenced by `assessments.user_id`
-   Referenced by `group_members.user_id`
-   Referenced by `curriculums.user_id`

### 2.2 Assessments Table [F-001]
Stores the results of AI-driven skill assessments.

```sql
CREATE TABLE assessments (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  scores JSONB NOT NULL, -- Detailed score breakdown
  level VARCHAR(50) NOT NULL, -- 'beginner', 'intermediate', 'advanced'
  collaboration_style VARCHAR(50), -- 'leader', 'builder', 'researcher'
  learning_goals TEXT[],
  recommended_paths TEXT[],
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_assessments_user_id ON assessments(user_id);
CREATE INDEX idx_assessments_level ON assessments(level);
CREATE INDEX idx_assessments_scores ON assessments USING GIN(scores);
```

**JSONB Schema (scores):**
```json
{
  "backend": 0.7,
  "frontend": 0.2,
  "ai_ml": 0.3,
  "mobile": 0.1,
  "devops": 0.4
}
```

### 2.3 Groups Table [F-002]
Manages learning group entities.

```sql
CREATE TABLE groups (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name VARCHAR(200),
  status VARCHAR(50) DEFAULT 'active', -- 'active', 'inactive', 'disbanded'
  matching_score JSONB, -- Metadata about why this group was formed
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_groups_status ON groups(status);
```

### 2.4 Group Members Table
Links users to groups with specific roles.

```sql
CREATE TABLE group_members (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  group_id UUID REFERENCES groups(id) ON DELETE CASCADE,
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  role VARCHAR(50), -- 'leader', 'member'
  joined_at TIMESTAMP DEFAULT NOW(),
  left_at TIMESTAMP,
  UNIQUE(group_id, user_id)
);

CREATE INDEX idx_group_members_group_id ON group_members(group_id);
CREATE INDEX idx_group_members_user_id ON group_members(user_id);
```

### 2.5 Projects Table [F-004]
Tracks project progress and metadata.

```sql
CREATE TABLE projects (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  group_id UUID REFERENCES groups(id) ON DELETE CASCADE,
  name VARCHAR(200) NOT NULL,
  description TEXT,
  tech_stack JSONB, -- Array of technologies used
  status VARCHAR(50) DEFAULT 'planning', -- 'planning', 'in_progress', 'review', 'completed'
  github_repo_url VARCHAR(500),
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_projects_group_id ON projects(group_id);
CREATE INDEX idx_projects_status ON projects(status);
CREATE INDEX idx_projects_tech_stack ON projects USING GIN(tech_stack);
```

### 2.6 Tasks Table
Manages individual work items within a project.

```sql
CREATE TABLE tasks (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID REFERENCES projects(id) ON DELETE CASCADE,
  title VARCHAR(200) NOT NULL,
  description TEXT,
  assignee_id UUID REFERENCES users(id),
  status VARCHAR(50) DEFAULT 'todo', -- 'todo', 'in_progress', 'done'
  priority VARCHAR(50) DEFAULT 'medium', -- 'low', 'medium', 'high'
  due_date TIMESTAMP,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_tasks_project_id ON tasks(project_id);
CREATE INDEX idx_tasks_assignee_id ON tasks(assignee_id);
CREATE INDEX idx_tasks_status ON tasks(status);
```

### 2.7 Curriculums Table [F-005]
Stores personalized learning paths.

```sql
CREATE TABLE curriculums (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  roadmap JSONB NOT NULL, -- The full curriculum structure
  current_week INTEGER DEFAULT 1,
  progress JSONB, -- Tracking completion status
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_curriculums_user_id ON curriculums(user_id);
CREATE INDEX idx_curriculums_roadmap ON curriculums USING GIN(roadmap);
```

**JSONB Schema (roadmap):**
```json
{
  "weeks": [
    {
      "week": 1,
      "goals": ["Learn basics"],
      "tasks": [...],
      "resources": [...]
    }
  ]
}
```

### 2.8 Portfolios Table [F-006]
Stores generated portfolio data.

```sql
CREATE TABLE portfolios (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  project_ids UUID[], -- Array of projects included
  template VARCHAR(50),
  content JSONB, -- The generated content
  public_url VARCHAR(500),
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_portfolios_user_id ON portfolios(user_id);
```

---

## 3. Entity Relationships

### ER Diagram Summary

-   **Users** have 1:N relationships with **Assessments**, **Group Members**, and **Portfolios**.
-   **Users** have a 1:1 relationship with **Curriculums**.
-   **Groups** have 1:N relationships with **Group Members** and **Projects**.
-   **Projects** have a 1:N relationship with **Tasks**.

---

## 4. Indexing Strategy

To ensure high performance, the following indexing strategies are applied:

-   **Primary Keys:** Automatically indexed (B-Tree).
-   **Foreign Keys:** Explicitly indexed to speed up joins.
-   **JSONB Fields:** GIN indexes used for `scores`, `tech_stack`, and `roadmap` to allow efficient querying within JSON documents.
-   **Status Fields:** Indexed to quickly filter active groups or projects.

---

## 5. Security Considerations

-   **Password Hashing:** Passwords are never stored in plain text; `bcrypt` or `Argon2` is used.
-   **Encryption:** Sensitive user data is encrypted at rest.
-   **RLS (Row Level Security):** Can be enabled for multi-tenant isolation if needed.

---

**Next Step:** Review [API Endpoints](api-endpoints.md).

