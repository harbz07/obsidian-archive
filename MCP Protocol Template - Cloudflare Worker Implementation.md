---
notion-id: 25298e9c-907e-817a-990c-ccf6fd91e2a4
---
This template provides a complete implementation of the Model Context Protocol (MCP) for Cloudflare Workers.
## Basic Worker Structure
```javascript
export default {
  async fetch(request, env, ctx) {
    // Handle CORS for MCP connections
    if (request.method === 'OPTIONS') {
      return new Response(null, {
        status: 200,
        headers: {
          'Access-Control-Allow-Origin': '*',
          'Access-Control-Allow-Methods': 'GET, POST, OPTIONS',
          'Access-Control-Allow-Headers': 'Content-Type',
        },
      });
    }

    // Only handle POST requests for MCP
    if (request.method !== 'POST') {
      return new Response('Method not allowed', { status: 405 });
    }

    try {
      const body = await request.json();
      const response = await handleMCPRequest(body, env);
      
      return new Response(JSON.stringify(response), {
        headers: {
          'Content-Type': 'application/json',
          'Access-Control-Allow-Origin': '*',
        },
      });
    } catch (error) {
      return new Response(JSON.stringify({
        jsonrpc: '2.0',
        error: {
          code: -32603,
          message: 'Internal error',
          data: error.message
        },
        id: null
      }), {
        status: 500,
        headers: {
          'Content-Type': 'application/json',
          'Access-Control-Allow-Origin': '*',
        },
      });
    }
  },
};
```
## MCP Request Handler
```javascript
async function handleMCPRequest(request, env) {
  const { method, params, id, jsonrpc } = request;
  
  // Validate JSON-RPC format
  if (jsonrpc !== '2.0') {
    return {
      jsonrpc: '2.0',
      error: {
        code: -32600,
        message: 'Invalid Request - must use JSON-RPC 2.0'
      },
      id
    };
  }

  try {
    let result;
    
    switch (method) {
      case 'initialize':
        result = await handleInitialize(params);
        break;
        
      case 'tools/list':
        result = await handleToolsList();
        break;
        
      case 'tools/call':
        result = await handleToolsCall(params, env);
        break;
        
      default:
        return {
          jsonrpc: '2.0',
          error: {
            code: -32601,
            message: `Unknown method: ${method}`
          },
          id
        };
    }
    
    return {
      jsonrpc: '2.0',
      result,
      id
    };
    
  } catch (error) {
    return {
      jsonrpc: '2.0',
      error: {
        code: -32603,
        message: 'Internal error',
        data: error.message
      },
      id
    };
  }
}
```
## Initialize Handler
```javascript
async function handleInitialize(params) {
  const { protocolVersion, capabilities, clientInfo } = params;
  
  return {
    protocolVersion: '2025-06-18',
    capabilities: {
      tools: {},
      resources: {},
      prompts: {},
      logging: {}
    },
    serverInfo: {
      name: 'knowledge-hub-mcp',
      version: '1.0.0'
    }
  };
}
```
## Tools List Handler
```javascript
async function handleToolsList() {
  return {
    tools: [
      {
        name: 'search_knowledge',
        description: 'Search through knowledge base entries',
        inputSchema: {
          type: 'object',
          properties: {
            query: {
              type: 'string',
              description: 'Search query'
            },
            limit: {
              type: 'number',
              description: 'Maximum number of results',
              default: 10
            }
          },
          required: ['query']
        }
      },
      {
        name: 'store_knowledge',
        description: 'Store new knowledge entry',
        inputSchema: {
          type: 'object',
          properties: {
            title: {
              type: 'string',
              description: 'Title of the knowledge entry'
            },
            content: {
              type: 'string',
              description: 'Content to store'
            },
            tags: {
              type: 'array',
              items: { type: 'string' },
              description: 'Optional tags for categorization'
            }
          },
          required: ['title', 'content']
        }
      }
    ]
  };
}
```
## Tools Call Handler
```javascript
async function handleToolsCall(params, env) {
  const { name, arguments: args } = params;
  
  switch (name) {
    case 'search_knowledge':
      return await searchKnowledge(args, env);
      
    case 'store_knowledge':
      return await storeKnowledge(args, env);
      
    default:
      throw new Error(`Unknown tool: ${name}`);
  }
}
```
## Knowledge Functions (using KV or D1)
```javascript
// Using Cloudflare KV
async function searchKnowledge(args, env) {
  const { query, limit = 10 } = args;
  
  // Simple implementation - in production you'd want better search
  const list = await env.KNOWLEDGE_KV.list({ prefix: 'entry:' });
  const results = [];
  
  for (const key of list.keys.slice(0, limit)) {
    const entry = await env.KNOWLEDGE_KV.get(key.name, 'json');
    if (entry && (entry.title.includes(query) || entry.content.includes(query))) {
      results.push(entry);
    }
  }
  
  return {
    content: [
      {
        type: 'text',
        text: `Found ${results.length} results for "${query}":\n\n${results.map(r => `**${r.title}**\n${r.content.substring(0, 200)}...`).join('\n\n')}`
      }
    ]
  };
}

async function storeKnowledge(args, env) {
  const { title, content, tags = [] } = args;
  
  const entry = {
    id: crypto.randomUUID(),
    title,
    content,
    tags,
    created: new Date().toISOString()
  };
  
  await env.KNOWLEDGE_KV.put(`entry:${entry.id}`, JSON.stringify(entry));
  
  return {
    content: [
      {
        type: 'text',
        text: `Successfully stored knowledge entry: "${title}"`
      }
    ]
  };
}
```
## Wrangler Configuration
Add to your `wrangler.toml`:
```toml
name = "knowledge-hub-mcp"
compatibility_date = "2024-08-16"
main = "src/index.js"

[[kv_namespaces]]
binding = "KNOWLEDGE_KV"
id = "your-kv-namespace-id"
preview_id = "your-preview-kv-namespace-id"
```
## Testing Your MCP Worker
### Test Initialize Request:
```bash
curl -X POST https://knowledge-hub-mcp.harveytagalicud7.workers.dev/mcp \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "initialize",
    "params": {
      "protocolVersion": "2025-06-18",
      "capabilities": {},
      "clientInfo": {"name": "test", "version": "1.0.0"}
    },
    "id": 1
  }'
```
### Test Tools List:
```bash
curl -X POST https://knowledge-hub-mcp.harveytagalicud7.workers.dev/mcp \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "tools/list",
    "params": {},
    "id": 2
  }'
```
## Debugging Tips
1. **Check Worker Logs**: Use `wrangler tail` to see real-time logs
2. **Test Locally**: Use `wrangler dev` for local development
3. **Validate JSON-RPC**: Ensure all responses follow JSON-RPC 2.0 format
4. **Handle CORS**: MCP remote connections need proper CORS headers
5. **Error Handling**: Always return proper error responses

## Common Issues
- **"Unknown method" errors**: Make sure your method handlers are correctly named
- **CORS issues**: Add proper Access-Control headers
- **JSON parsing errors**: Validate request format
- **Environment variables**: Ensure KV/D1 bindings are configured

## Next Steps
6. Deploy this template to your Worker
7. Test the endpoints manually
8. Configure Claude Desktop to connect
9. Add your specific knowledge base functionality