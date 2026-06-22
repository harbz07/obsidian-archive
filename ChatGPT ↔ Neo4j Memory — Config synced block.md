```json
{
  "provider": "openai",
  "model": "gpt-4.1",
  "mcp": "neo4j-memory",
  "server_url": "https://server.smithery.ai/@sylweriusz/mcp-neo4j-memory-server/mcp",
  "auth": {"type": "bearer", "env": "OPENAI_API_KEY"},
  "routing": {"context_budget": 64000, "compression": "map-reduce"},
  "limits": {"rate_rps": 3, "tokens_max": 128000},
  "timeouts_ms": 30000,
  "capabilities": ["tools", "function_calling", "streaming"]
}
```