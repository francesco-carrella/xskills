---
name: archon-api
description: This skill provides Archon knowledge management API operations for RAG search, project/task management, document handling, and crawling. Use this skill when the user needs to search the knowledge base, manage projects or tasks, crawl documentation, or interact with the Archon system.
---

# Archon Knowledge Management

Archon is a knowledge management and task tracking system accessible via REST API.

**Base URL**: `http://100.91.166.2:8181`

## Quick Start

```bash
# Health check
curl -s http://100.91.166.2:8181/api/health

# Search knowledge base
curl -s -X POST http://100.91.166.2:8181/api/rag/query \
  -H "Content-Type: application/json" \
  -d '{"query": "search term", "match_count": 5}'
```

## Operation Categories

| Category | Description | Reference |
|----------|-------------|-----------|
| **RAG** | Search knowledge base, code examples | [references/rag.md](references/rag.md) |
| **Projects & Tasks** | CRUD for projects and tasks | [references/projects-tasks.md](references/projects-tasks.md) |
| **Crawling** | Crawl docs, upload documents | [references/crawling.md](references/crawling.md) |
| **System** | Credentials, versions, providers | [references/system.md](references/system.md) |

## Common Workflows

### Research a Topic

```bash
# 1. Search knowledge base
curl -s -X POST http://100.91.166.2:8181/api/rag/query \
  -H "Content-Type: application/json" \
  -d '{"query": "authentication patterns", "match_count": 5}'

# 2. Find code examples
curl -s -X POST http://100.91.166.2:8181/api/rag/code-examples \
  -H "Content-Type: application/json" \
  -d '{"query": "JWT auth", "match_count": 5}'

# 3. Read full page for context
curl -s http://100.91.166.2:8181/api/pages/PAGE_ID
```

### Work on a Task

```bash
# 1. Find available tasks
curl -s "http://100.91.166.2:8181/api/tasks?status=todo"

# 2. Start working
curl -s -X PUT http://100.91.166.2:8181/api/tasks/TASK_ID \
  -H "Content-Type: application/json" \
  -d '{"status": "doing", "assignee": "User"}'

# 3. Complete task
curl -s -X PUT http://100.91.166.2:8181/api/tasks/TASK_ID \
  -H "Content-Type: application/json" \
  -d '{"status": "done"}'
```

## Quick Reference

### RAG Search
```bash
curl -s -X POST http://100.91.166.2:8181/api/rag/query \
  -H "Content-Type: application/json" \
  -d '{"query": "TERM", "match_count": 5}'

curl -s http://100.91.166.2:8181/api/rag/sources
```

### Projects
```bash
curl -s http://100.91.166.2:8181/api/projects
curl -s http://100.91.166.2:8181/api/projects/ID
curl -s -X POST http://100.91.166.2:8181/api/projects \
  -H "Content-Type: application/json" \
  -d '{"title": "Name", "description": "Desc"}'
```

### Tasks
```bash
curl -s http://100.91.166.2:8181/api/tasks
curl -s "http://100.91.166.2:8181/api/tasks?status=todo"
curl -s -X POST http://100.91.166.2:8181/api/tasks \
  -H "Content-Type: application/json" \
  -d '{"project_id": "ID", "title": "Task", "status": "todo"}'
```

## Response Parsing

```bash
# List project titles
curl -s http://100.91.166.2:8181/api/projects | jq '.projects[].title'

# Get task info
curl -s http://100.91.166.2:8181/api/tasks | jq '.tasks[] | {id, title, status}'

# List RAG sources
curl -s http://100.91.166.2:8181/api/rag/sources | jq '.sources[] | {source_id, title}'
```

## Query Tips

- Keep queries SHORT (2-5 keywords)
- Good: "vector search pgvector", "authentication JWT"
- Bad: "how to implement vector search with pgvector in PostgreSQL..."

## Task Status Flow

```
todo → doing → review → done
```

- Only ONE task should be `doing` at a time
- Use `review` for work awaiting validation
