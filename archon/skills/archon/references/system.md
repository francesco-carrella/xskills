# System Operations

## Credentials

```bash
# List all
curl -s http://100.91.166.2:8181/api/credentials

# Get by category
curl -s http://100.91.166.2:8181/api/credentials/categories/CATEGORY

# Get specific
curl -s http://100.91.166.2:8181/api/credentials/KEY

# Set credential
curl -s -X POST http://100.91.166.2:8181/api/credentials \
  -H "Content-Type: application/json" \
  -d '{
    "key": "CREDENTIAL_KEY",
    "value": "value",
    "category": "api_keys"
  }'

# Initialize
curl -s -X POST http://100.91.166.2:8181/api/credentials/initialize

# Status check
curl -s http://100.91.166.2:8181/api/credentials/status-check
```

## Version & System

```bash
# Current version
curl -s http://100.91.166.2:8181/api/version/current

# Check for updates
curl -s http://100.91.166.2:8181/api/version/check

# Clear cache
curl -s -X POST http://100.91.166.2:8181/api/version/clear-cache

# Database metrics
curl -s http://100.91.166.2:8181/api/database/metrics

# Settings health
curl -s http://100.91.166.2:8181/api/settings/health
```

## Migrations

```bash
curl -s http://100.91.166.2:8181/api/migrations/status
curl -s http://100.91.166.2:8181/api/migrations/pending
curl -s http://100.91.166.2:8181/api/migrations/history
```

## Providers

```bash
# Check provider status
curl -s http://100.91.166.2:8181/api/providers/PROVIDER/status
```

**Providers**: `openai`, `anthropic`, `ollama`

## Ollama

```bash
# List models
curl -s http://100.91.166.2:8181/api/ollama/models
curl -s http://100.91.166.2:8181/api/ollama/models/stored

# Discover
curl -s -X POST http://100.91.166.2:8181/api/ollama/models/discover-and-store
curl -s http://100.91.166.2:8181/api/ollama/models/discover-with-details

# Test capabilities
curl -s -X POST http://100.91.166.2:8181/api/ollama/models/test-capabilities \
  -H "Content-Type: application/json" \
  -d '{"model": "MODEL_NAME"}'

# Validate & health
curl -s http://100.91.166.2:8181/api/ollama/validate
curl -s http://100.91.166.2:8181/api/ollama/instances/health

# Embedding
curl -s http://100.91.166.2:8181/api/ollama/embedding/routes
curl -s http://100.91.166.2:8181/api/ollama/embedding/route

# Cache
curl -s http://100.91.166.2:8181/api/ollama/cache
```

## MCP Server

```bash
curl -s http://100.91.166.2:8181/api/mcp/status
curl -s http://100.91.166.2:8181/api/mcp/health
curl -s http://100.91.166.2:8181/api/mcp/clients
curl -s http://100.91.166.2:8181/api/mcp/sessions
curl -s http://100.91.166.2:8181/api/mcp/config
curl -s http://100.91.166.2:8181/api/mcp/tasks/TASK_ID/status
```

## Bug Reports

```bash
# Submit to GitHub
curl -s -X POST http://100.91.166.2:8181/api/bug-report/github \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Bug title",
    "description": "Description",
    "steps_to_reproduce": ["Step 1", "Step 2"]
  }'

# Health
curl -s http://100.91.166.2:8181/api/bug-report/health
```
