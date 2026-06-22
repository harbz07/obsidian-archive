---
notion-id: 25298e9c-907e-8102-a1a1-e0a51a6bb502
---
# MCP For Dummies: Complete Setup Guide
## What is MCP?
Model Context Protocol (MCP) is like **USB-C for AI applications**. Instead of building custom connectors for every AI app + tool combination, MCP provides one standard that works everywhere.
### Before MCP: The N×M Problem
- **N** AI apps (Claude, ChatGPT, custom agents)
- **M** tools (GitHub, Slack, databases)
- Required **N×M** custom integrations 😵

### With MCP: N+M Solution
- **N** MCP clients (one per AI app)
- **M** MCP servers (one per tool)
- Total: **N+M** integrations 🎉

---
## MCP vs OpenAI Function Calling

| Feature | MCP | OpenAI Functions |
| --- | --- | --- |
| **Protocol** | JSON-RPC over stdio/HTTP | HTTP with function schemas |
| **Components** | Tools + Resources + Prompts | Just function calls |
| **State** | Stateful sessions | Stateless |
| **Best For** | Complex workflows, persistent context | Simple API interactions |
| **Support** | Claude Desktop, growing ecosystem | OpenAI APIs, ChatGPT |

---
## Installation Methods
### 🚀 Method 1: DXT Extensions (Recommended)
**What are DXT files?**
- ZIP archives containing MCP server + configuration
- Like Chrome extensions but for MCP servers
- One-click installation!

**Steps:**
1. Download `.dxt` file
2. Double-click to install
3. Configure in Claude Desktop Settings > Extensions
4. Start using immediately

### ⚙️ Method 2: Manual MCP Setup
**Prerequisites:**
- Node.js or Python installed
- Text editor

**Steps:**
5. Install MCP server: `npm install -g your-mcp-server`
6. Edit `~/.claude/claude_desktop_config.json`:
```json
{
  "mcpServers": {
    "server-name": {
      "command": "npx",
      "args": ["your-mcp-server"]
    }
  }
}
```
7. Restart Claude Desktop

### 🔧 Method 3: OpenAI Function Calling
**For ChatGPT/OpenAI API:**
8. Define function schemas
9. Implement HTTP endpoints
10. Use `tools` parameter in API calls

---
## DXT Extension Structure
```javascript
my-extension.dxt (ZIP file)
├── manifest.json          # Required: Extension metadata
├── server/
│   ├── index.js          # Main MCP server
│   └── package.json      # Dependencies
├── node_modules/         # Bundled dependencies  
├── icon.png             # Optional: Extension icon
└── README.md            # Documentation
```
### Sample manifest.json
```json
{
  "dxt_version": "0.1",
  "name": "khub-desktop",
  "version": "1.0.0",
  "description": "Local knowledge hub with dual AI compatibility",
  "author": {
    "name": "Harvey",
    "email": "harvey@example.com"
  },
  "server": {
    "type": "node",
    "entry_point": "server/index.js",
    "mcp_config": {
      "command": "node",
      "args": ["server/index.js"]
    }
  },
  "user_config": {
    "storage_path": {
      "type": "directory",
      "title": "Knowledge Storage Directory",
      "description": "Where to store your knowledge database",
      "required": false,
      "default": "${HOME}/.khub"
    }
  }
}
```

---
## Building Dual-Compatible Servers
### Tool Schema Compatibility
**MCP Tool:**
```typescript
{
  name: "search_knowledge",
  description: "Search stored knowledge",
  inputSchema: {
    type: "object",
    properties: {
      query: { type: "string" },
      tags: { type: "array", items: { type: "string" } }
    },
    required: ["query"]
  }
}
```
**OpenAI Function:**
```typescript
{
  name: "search_knowledge", 
  description: "Search stored knowledge",
  parameters: {
    type: "object",
    properties: {
      query: { type: "string" },
      tags: { type: "array", items: { type: "string" } }
    },
    required: ["query"]
  }
}
```
**Key Difference:** MCP uses `inputSchema`, OpenAI uses `parameters`

---
## Security Best Practices
### 🔒 MCP Servers
- Validate all inputs from untrusted sources
- Implement explicit user consent for sensitive operations
- Use OS keychain for credentials
- Sandbox file access to specific directories

### 🛡️ OpenAI Functions
- Server-side validation of all calls
- Rate limiting to prevent abuse
- Authentication for sensitive functions
- User confirmation for destructive actions

---
## Troubleshooting
### 🐛 Common Issues
**MCP Server Won't Start:**
- Check Claude Desktop logs (Settings > Extensions)
- Verify `manifest.json` syntax
- Ensure dependencies are bundled
- Check file permissions

**Function Not Called:**
- Review function descriptions for clarity
- Verify JSON schema is valid
- Test with simpler examples first

**Permission Errors:**
- Verify filesystem permissions in manifest
- Check user granted required access
- Ensure paths exist and are accessible

---
## Development Tools
### 🛠️ DXT CLI
```bash
# Install
npm install -g @anthropic-ai/dxt

# Create project
dxt init

# Package extension
dxt pack
```
### 🔍 MCP Inspector
```bash
# Test MCP server
npx @modelcontextprotocol/inspector server/index.js
```

---
## Resources
### 📚 Official Docs
- [MCP Specification](https://spec.modelcontextprotocol.io/)
- [MCP GitHub](https://github.com/modelcontextprotocol)
- [DXT Documentation](https://github.com/anthropics/dxt)
- [OpenAI Function Calling](https://platform.openai.com/docs/guides/function-calling)

### 🌟 Community
- [Awesome MCP Servers](https://github.com/punkpeye/awesome-mcp-servers)
- [DXT Extension Directory](https://mcp.so/dxt)
- [MCP Discussions](https://github.com/modelcontextprotocol/discussions)

---
## Quick Start Checklist
- [ ] Install Claude Desktop (latest version)
- [ ] Download or build a `.dxt` extension
- [ ] Double-click to install
- [ ] Configure permissions in Settings > Extensions
- [ ] Test with a simple query
- [ ] Build your own extensions with the provided build script!

---
*Updated: August 2025 | MCP v1.0+ | DXT v0.1+*