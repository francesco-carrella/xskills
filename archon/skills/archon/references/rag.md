# RAG / Knowledge Base

## Search Knowledge Base

```bash
curl -s -X POST http://100.91.166.2:8181/api/rag/query \
  -H "Content-Type: application/json" \
  -d '{
    "query": "YOUR_SEARCH_QUERY",
    "source_id": "OPTIONAL_SOURCE_ID",
    "match_count": 5
  }'
```

## Search Code Examples

```bash
# Via RAG endpoint (with reranking)
curl -s -X POST http://100.91.166.2:8181/api/rag/code-examples \
  -H "Content-Type: application/json" \
  -d '{"query": "YOUR_QUERY", "match_count": 5}'

# Simplified endpoint
curl -s -X POST http://100.91.166.2:8181/api/code-examples \
  -H "Content-Type: application/json" \
  -d '{"query": "YOUR_QUERY", "match_count": 5}'
```

## List Sources

```bash
curl -s http://100.91.166.2:8181/api/rag/sources
```

## Pages

```bash
# Get page by ID
curl -s http://100.91.166.2:8181/api/pages/PAGE_ID

# Get page by URL
curl -s "http://100.91.166.2:8181/api/pages/by-url?url=ENCODED_URL"

# List pages for source
curl -s "http://100.91.166.2:8181/api/pages?source_id=SOURCE_ID"
```

## Knowledge Items

```bash
# List with pagination
curl -s "http://100.91.166.2:8181/api/knowledge-items?page=1&per_page=20"

# Filter by type
curl -s "http://100.91.166.2:8181/api/knowledge-items?knowledge_type=technical"

# Search
curl -s "http://100.91.166.2:8181/api/knowledge-items?search=TERM"

# List sources
curl -s http://100.91.166.2:8181/api/knowledge-items/sources

# Get source details
curl -s http://100.91.166.2:8181/api/knowledge-items/SOURCE_ID

# Get chunks
curl -s http://100.91.166.2:8181/api/knowledge-items/SOURCE_ID/chunks

# Get code examples for source
curl -s http://100.91.166.2:8181/api/knowledge-items/SOURCE_ID/code-examples

# Summary
curl -s http://100.91.166.2:8181/api/knowledge-items/summary

# Search
curl -s -X POST http://100.91.166.2:8181/api/knowledge-items/search \
  -H "Content-Type: application/json" \
  -d '{"query": "TERM"}'

# Delete source
curl -s -X DELETE http://100.91.166.2:8181/api/sources/SOURCE_ID
```
