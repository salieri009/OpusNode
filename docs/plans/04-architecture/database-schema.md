# 💾 Database Schema

**Document:** TailCamp PRD - Database Schema  
**Version:** 1.0  
**Last Updated:** 2025-11-15

---

## 📋 Overview

TailCamp의 데이터베이스 스키마 설계입니다. PostgreSQL을 주 데이터베이스로 사용합니다.

**관련 문서:**
- [System Architecture](system-architecture.md) - 시스템 아키텍처
- [Technology Stack](technology-stack.md) - 기술 스택

---

## 📊 Core Tables

### Users Table

사용자 기본 정보를 저장합니다.

```sql
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) UNIQUE NOT NULL,
  name VARCHAR(100) NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  role VARCHAR(50) DEFAULT 'user',
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_role ON users(role);
```

**관계:**
- `assessments.user_id` → Foreign Key
- `group_members.user_id` → Foreign Key
- `curriculums.user_id` → Foreign Key

---

### Assessments Table

AI 인터뷰 평가 결과를 저장합니다.

```sql
CREATE TABLE assessments (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  scores JSONB NOT NULL,
  level VARCHAR(50) NOT NULL,
  collaboration_style VARCHAR(50),
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

---

### Groups Table

학습 그룹 정보를 저장합니다.

```sql
CREATE TABLE groups (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name VARCHAR(200),
  status VARCHAR(50) DEFAULT 'active',
  matching_score JSONB,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_groups_status ON groups(status);
```

**Status Values:**
- `active`: 활성 그룹
- `inactive`: 비활성 그룹
- `disbanded`: 해체된 그룹

---

### Group Members Table

그룹 구성원 정보를 저장합니다.

```sql
CREATE TABLE group_members (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  group_id UUID REFERENCES groups(id) ON DELETE CASCADE,
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  role VARCHAR(50),
  joined_at TIMESTAMP DEFAULT NOW(),
  left_at TIMESTAMP,
  UNIQUE(group_id, user_id)
);

CREATE INDEX idx_group_members_group_id ON group_members(group_id);
CREATE INDEX idx_group_members_user_id ON group_members(user_id);
```

---

### Projects Table

그룹 프로젝트 정보를 저장합니다.

```sql
CREATE TABLE projects (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  group_id UUID REFERENCES groups(id) ON DELETE CASCADE,
  name VARCHAR(200) NOT NULL,
  description TEXT,
  tech_stack JSONB,
  status VARCHAR(50) DEFAULT 'planning',
  github_repo_url VARCHAR(500),
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_projects_group_id ON projects(group_id);
CREATE INDEX idx_projects_status ON projects(status);
CREATE INDEX idx_projects_tech_stack ON projects USING GIN(tech_stack);
```

**Status Values:**
- `planning`: 기획 중
- `in_progress`: 진행 중
- `review`: 리뷰 중
- `completed`: 완료

---

### Tasks Table

프로젝트 태스크를 저장합니다.

```sql
CREATE TABLE tasks (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID REFERENCES projects(id) ON DELETE CASCADE,
  title VARCHAR(200) NOT NULL,
  description TEXT,
  assignee_id UUID REFERENCES users(id),
  status VARCHAR(50) DEFAULT 'todo',
  priority VARCHAR(50) DEFAULT 'medium',
  due_date TIMESTAMP,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_tasks_project_id ON tasks(project_id);
CREATE INDEX idx_tasks_assignee_id ON tasks(assignee_id);
CREATE INDEX idx_tasks_status ON tasks(status);
```

---

### Curriculums Table

개인화된 커리큘럼을 저장합니다.

```sql
CREATE TABLE curriculums (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  roadmap JSONB NOT NULL,
  current_week INTEGER DEFAULT 1,
  progress JSONB,
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

---

### Portfolios Table

생성된 포트폴리오를 저장합니다.

```sql
CREATE TABLE portfolios (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  project_ids UUID[],
  template VARCHAR(50),
  content JSONB,
  public_url VARCHAR(500),
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_portfolios_user_id ON portfolios(user_id);
```

---

## 🔗 Relationships

### Entity Relationship Diagram (ERD)

```
users
  ├── assessments (1:N)
  ├── group_members (1:N)
  ├── curriculums (1:1)
  └── portfolios (1:N)

groups
  ├── group_members (1:N)
  └── projects (1:N)

projects
  └── tasks (1:N)
```

---

## 📊 Indexes

### Performance Optimization
- Primary keys: 자동 인덱스
- Foreign keys: 인덱스 생성
- JSONB fields: GIN 인덱스
- Frequently queried fields: B-tree 인덱스

---

## 🔐 Security Considerations

### Data Protection
- Password hashing: SHA-256 with salt
- Sensitive data: Encryption at rest
- Access control: Row-level security (선택적)

---

## 🔗 관련 문서

- [System Architecture](system-architecture.md) - 시스템 아키텍처
- [API Endpoints](api-endpoints.md) - API 엔드포인트
- [Technology Stack](technology-stack.md) - 기술 스택

---

**다음 단계:** [API Endpoints](api-endpoints.md) 확인

