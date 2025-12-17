# Crawling & Document Upload

## Start a Crawl

```bash
curl -s -X POST http://100.91.166.2:8181/api/knowledge-items/crawl \
  -H "Content-Type: application/json" \
  -d '{
    "url": "https://example.com/docs",
    "title": "Example Docs",
    "crawl_type": "llms_txt"
  }'
```

**Crawl types**:
- `llms_txt` - Parse llms.txt file
- `llms_txt_with_linked_pages` - llms.txt + linked pages
- `single_page` - Single page only
- `sitemap` - Parse sitemap.xml

## Refresh Source

```bash
curl -s -X POST http://100.91.166.2:8181/api/knowledge-items/SOURCE_ID/refresh
```

## Check Progress

```bash
curl -s http://100.91.166.2:8181/api/crawl-progress/PROGRESS_ID
```

## Stop Crawl

```bash
curl -s -X POST http://100.91.166.2:8181/api/knowledge-items/stop/PROGRESS_ID
```

## Upload Document

```bash
curl -s -X POST http://100.91.166.2:8181/api/documents/upload \
  -F "file=@/path/to/document.pdf" \
  -F "title=Document Title" \
  -F "source_type=pdf"
```

## Progress Tracking

```bash
# List all progress operations
curl -s http://100.91.166.2:8181/api/progress/

# Get specific progress
curl -s http://100.91.166.2:8181/api/progress/OPERATION_ID
```

## Agent Chat Sessions

```bash
# List sessions
curl -s http://100.91.166.2:8181/api/agent-chat/sessions

# Get session
curl -s http://100.91.166.2:8181/api/agent-chat/sessions/SESSION_ID

# Get messages
curl -s http://100.91.166.2:8181/api/agent-chat/sessions/SESSION_ID/messages

# Create session
curl -s -X POST http://100.91.166.2:8181/api/agent-chat/sessions \
  -H "Content-Type: application/json" \
  -d '{"title": "Session", "context": {}}'

# Add message
curl -s -X POST http://100.91.166.2:8181/api/agent-chat/sessions/SESSION_ID/messages \
  -H "Content-Type: application/json" \
  -d '{"role": "user", "content": "Message"}'
```
