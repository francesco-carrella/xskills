# Projects & Tasks

## Projects

### List & Get
```bash
curl -s http://100.91.166.2:8181/api/projects
curl -s http://100.91.166.2:8181/api/projects/PROJECT_ID
curl -s http://100.91.166.2:8181/api/projects/PROJECT_ID/features
curl -s http://100.91.166.2:8181/api/projects/health
curl -s http://100.91.166.2:8181/api/projects/task-counts
```

### Create
```bash
curl -s -X POST http://100.91.166.2:8181/api/projects \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Project Title",
    "description": "Description",
    "github_repo": "https://github.com/org/repo"
  }'
```

### Update
```bash
curl -s -X PUT http://100.91.166.2:8181/api/projects/PROJECT_ID \
  -H "Content-Type: application/json" \
  -d '{"title": "New Title", "description": "New desc"}'
```

### Delete
```bash
curl -s -X DELETE http://100.91.166.2:8181/api/projects/PROJECT_ID
```

## Tasks

### List & Filter
```bash
curl -s http://100.91.166.2:8181/api/tasks
curl -s "http://100.91.166.2:8181/api/tasks?status=todo"
curl -s "http://100.91.166.2:8181/api/tasks?status=doing"
curl -s "http://100.91.166.2:8181/api/tasks?status=review"
curl -s "http://100.91.166.2:8181/api/tasks?status=done"
curl -s "http://100.91.166.2:8181/api/tasks?project_id=PROJECT_ID"
curl -s "http://100.91.166.2:8181/api/tasks?query=SEARCH_TERM"
curl -s http://100.91.166.2:8181/api/projects/PROJECT_ID/tasks
```

### Get
```bash
curl -s http://100.91.166.2:8181/api/tasks/TASK_ID
```

### Create
```bash
curl -s -X POST http://100.91.166.2:8181/api/tasks \
  -H "Content-Type: application/json" \
  -d '{
    "project_id": "PROJECT_UUID",
    "title": "Task title",
    "description": "Description",
    "status": "todo",
    "assignee": "User",
    "feature": "feature-name",
    "task_order": 50
  }'
```

**Status values**: `todo`, `doing`, `review`, `done`
**Assignee**: "User", "Archon", "Coding Agent", or custom

### Update
```bash
curl -s -X PUT http://100.91.166.2:8181/api/tasks/TASK_ID \
  -H "Content-Type: application/json" \
  -d '{"status": "doing", "assignee": "User"}'
```

### Delete
```bash
curl -s -X DELETE http://100.91.166.2:8181/api/tasks/TASK_ID
```

## Documents

### List & Get
```bash
curl -s http://100.91.166.2:8181/api/projects/PROJECT_ID/docs
curl -s "http://100.91.166.2:8181/api/projects/PROJECT_ID/docs?document_type=spec"
curl -s http://100.91.166.2:8181/api/projects/PROJECT_ID/docs/DOC_ID
```

**Document types**: `spec`, `design`, `note`, `prp`, `api`, `guide`

### Create
```bash
curl -s -X POST http://100.91.166.2:8181/api/projects/PROJECT_ID/docs \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Document Title",
    "document_type": "spec",
    "content": {"sections": [{"title": "Overview", "body": "..."}]},
    "tags": ["backend"],
    "author": "User"
  }'
```

### Update & Delete
```bash
curl -s -X PUT http://100.91.166.2:8181/api/projects/PROJECT_ID/docs/DOC_ID \
  -H "Content-Type: application/json" \
  -d '{"content": {"updated": "content"}}'

curl -s -X DELETE http://100.91.166.2:8181/api/projects/PROJECT_ID/docs/DOC_ID
```

## Versions

```bash
# List versions
curl -s http://100.91.166.2:8181/api/projects/PROJECT_ID/versions
curl -s "http://100.91.166.2:8181/api/projects/PROJECT_ID/versions?field_name=docs"

# Get specific version
curl -s http://100.91.166.2:8181/api/projects/PROJECT_ID/versions/FIELD/VERSION

# Create snapshot
curl -s -X POST http://100.91.166.2:8181/api/projects/PROJECT_ID/versions \
  -H "Content-Type: application/json" \
  -d '{
    "field_name": "docs",
    "content": [...],
    "change_summary": "Updated docs",
    "created_by": "User"
  }'

# Restore version
curl -s -X POST http://100.91.166.2:8181/api/projects/PROJECT_ID/versions/FIELD/VERSION/restore
```

**Field names**: `docs`, `features`, `data`, `prd`
