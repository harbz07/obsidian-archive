```json
{
  "provider": "anthropic",
  "model": "claude-3.5",
  "mcp": "neo4j-memory",
  "server_url": "https://server.smithery.ai/@sylweriusz/mcp-neo4j-memory-server/mcp",
  "auth": {"type": "bearer", "env": "ANTHROPIC_API_KEY"},
  "routing": {"context_budget": 120000, "compression": "semantic-chunk"},
  "limits": {"rate_rps": 2, "tokens_max": 200000},
  "timeouts_ms": 30000,
  "capabilities": ["tool_use", "json_mode", "streaming"]
}
```