# API CONTRACT ROADMAP

> > Only **Sprint 2 contracts** in this document are implemented today.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# API Contract Evolution Roadmap

> Only **Sprint 2 contracts** in this document are implemented today. Later sections
> (Sprint 3+) are a forward-looking roadmap and may not reflect the current code.

**Purpose**: Track planned API enhancements across sprints to prevent refactoring.

**Philosophy**: Additive changes only - never break existing contracts.

---

## Sprint 2 (Current): Foundation Contract ✅

**Endpoints:**
- `GET /api/projects/{id}/prd`
- `GET /api/projects/{id}/issues?include=tasks`

**Key Decisions:**
- ✅ IDs as `string` (future UUID support)
- ✅ RFC 3339 timestamps (`created_at`, `updated_at`, `completed_at`)
- ✅ `depends_on: string[]` (array, not single value)
- ✅ `proposed_by: 'agent' | 'human'` (provenance foundation)
- ✅ Pagination structure ready (`next_cursor`, `prev_cursor`)

**TypeScript Contract:**
```typescript
export type ISODate = string; // RFC 3339
export type WorkStatus = 'pending' | 'assigned' | 'in_progress' | 'blocked' | 'completed' | 'failed';

export interface Task {
  id: string;
  task_number: string;
  title: string;
  description: string;
  status: WorkStatus;
  depends_on: string[];
  proposed_by: 'agent' | 'human';
  created_at: ISODate;
  updated_at: ISODate;
  completed_at: ISODate | null;
}

export interface Issue {
  id: string;
  issue_number: string;
  title: string;
  description: string;
  status: WorkStatus;
  priority: number; // 0-4
  depends_on: string[];
  proposed_by: 'agent' | 'human';
  created_at: ISODate;
  updated_at: ISODate;
  completed_at: ISODate | null;
  tasks?: Task[]; // Conditional on include=tasks
}

export interface PRDResponse {
  project_id: string;
  prd_content: string;
  generated_at: ISODate;
  updated_at: ISODate;
  status: 'available' | 'generating' | 'not_found';
}

export interface IssuesResponse {
  issues: Issue[];
  total_issues: number;
  total_tasks: number;
  next_cursor?: string;
  prev_cursor?: string;
}
```

---

## Sprint 3: Agent Metadata & Filtering 🔜

**New Endpoints:**

*[truncated — see source for full prompt]*