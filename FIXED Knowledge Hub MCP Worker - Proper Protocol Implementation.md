---
notion-id: 25298e9c-907e-81d5-864e-d85ee0f02319
---
# 🚀 FIXED: Knowledge Hub MCP Worker
**Issue Diagnosed**: Your worker was using custom methods instead of standard MCP protocol methods.
**Solution**: Updated to handle standard MCP methods while keeping your sophisticated functionality.
## Replace Your Worker Code With This:
```javascript
/**
 * Knowledge Hub MCP - Fixed for Claude Desktop Integration
 * 
 * This implements proper MCP protocol while keeping your sophisticated
 * context engine functionality.
 */

export default {
  async fetch(request, env, ctx) {
    const url = new URL(request.url);
    
    // CORS headers for Claude.ai integration
    const corsHeaders = {
      'Access-Control-Allow-Origin': '*',
      'Access-Control-Allow-Methods': 'GET, POST, OPTIONS',
      'Access-Control-Allow-Headers': 'Content-Type',
    };
    
    // Handle CORS preflight
    if (request.method === 'OPTIONS') {
      return new Response(null, { headers: corsHeaders });
    }
    
    // MCP Protocol endpoint
    if (url.pathname === '/mcp' && request.method === 'POST') {
      try {
        const body = await request.json();
        const response = await handleMCPRequest(body, env);
        
        return new Response(JSON.stringify(response), {
          headers: { 
            ...corsHeaders, 
            'Content-Type': 'application/json'
          }
        });
      } catch (error) {
        console.error('MCP Error:', error);
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
            ...corsHeaders, 
            'Content-Type': 'application/json'
          }
        });
      }
    }
    
    // Health check
    if (url.pathname === '/health') {
      return new Response(JSON.stringify({
        status: 'healthy',
        timestamp: Date.now(),
        version: '2.0.0',
        protocol: 'MCP-compliant'
      }), {
        headers: { ...corsHeaders, 'Content-Type': 'application/json' }
      });
    }
    
    // Welcome page
    return new Response(`
      <!DOCTYPE html>
      <html>
      <head>
        <title>Knowledge Hub MCP</title>
        <style>
          body { font-family: system-ui; max-width: 800px; margin: 50px auto; padding: 20px; }
          .status { color: #22c55e; font-weight: bold; }
          .endpoint { background: #f3f4f6; padding: 10px; border-radius: 5px; margin: 10px 0; font-family: monospace; }
        </style>
      </head>
      <body>
        <h1>🧠 Knowledge Hub MCP</h1>
        <p class="status">✅ MCP Protocol Ready</p>
        
        <h3>MCP Tools Available:</h3>
        <div class="endpoint">query_context - Intelligent context retrieval</div>
        <div class="endpoint">store_segment - Store knowledge segments</div>
        <div class="endpoint">optimize_context - ADHD-aware context optimization</div>
        <div class="endpoint">get_session - Session management</div>
        
        <p>Ready for Claude Desktop integration!</p>
      </body>
      </html>
    `, {
      headers: { ...corsHeaders, 'Content-Type': 'text/html' }
    });
  }
};

// ============================================================================
// MCP PROTOCOL HANDLER (FIXED)
// ============================================================================

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
      // ===== STANDARD MCP METHODS (REQUIRED) =====
      case 'initialize':
        result = await handleInitialize(params);
        break;
        
      case 'tools/list':
        result = await handleToolsList();
        break;
        
      case 'tools/call':
        result = await handleToolsCall(params, env);
        break;
        
      // ===== LEGACY METHODS (KEEPING FOR COMPATIBILITY) =====
      case 'knowledge_hub/query_context':
        result = await queryContext(params, env);
        break;
        
      case 'knowledge_hub/store_segment':
        result = await storeSegment(params, env);
        break;
        
      case 'knowledge_hub/optimize_context':
        result = await optimizeContext(params, env);
        break;
        
      case 'knowledge_hub/get_session':
        result = await getSession(params, env);
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
    console.error('Method error:', error);
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

// ============================================================================
// STANDARD MCP METHODS
// ============================================================================

async function handleInitialize(params) {
  return {
    protocolVersion: '2025-06-18',
    capabilities: {
      tools: {}
    },
    serverInfo: {
      name: 'knowledge-hub-mcp',
      version: '2.0.0'
    }
  };
}

async function handleToolsList() {
  return {
    tools: [
      {
        name: 'query_context',
        description: 'Retrieve relevant context using ADHD-aware intelligent scoring',
        inputSchema: {
          type: 'object',
          properties: {
            query: {
              type: 'string',
              description: 'Query to search for relevant context'
            },
            maxTokens: {
              type: 'number',
              description: 'Maximum tokens to return',
              default: 2048
            },
            sessionId: {
              type: 'string',
              description: 'Session identifier for context persistence',
              default: 'default'
            }
          },
          required: ['query']
        }
      },
      {
        name: 'store_segment',
        description: 'Store a knowledge segment with intelligent categorization',
        inputSchema: {
          type: 'object',
          properties: {
            content: {
              type: 'string',
              description: 'Content to store'
            },
            metadata: {
              type: 'object',
              description: 'Additional metadata (tags, importance, etc.)'
            },
            sessionId: {
              type: 'string',
              description: 'Session identifier',
              default: 'default'
            }
          },
          required: ['content']
        }
      },
      {
        name: 'optimize_context',
        description: 'Apply ADHD-aware context optimization and intelligent shedding',
        inputSchema: {
          type: 'object',
          properties: {
            sessionId: {
              type: 'string',
              description: 'Session to optimize',
              default: 'default'
            },
            targetTokens: {
              type: 'number',
              description: 'Target token count after optimization',
              default: 50000
            }
          }
        }
      },
      {
        name: 'get_session',
        description: 'Get session information and statistics',
        inputSchema: {
          type: 'object',
          properties: {
            sessionId: {
              type: 'string',
              description: 'Session identifier',
              default: 'default'
            }
          }
        }
      }
    ]
  };
}

async function handleToolsCall(params, env) {
  const { name, arguments: args } = params;
  
  switch (name) {
    case 'query_context':
      return await queryContext(args, env);
      
    case 'store_segment':
      return await storeSegment(args, env);
      
    case 'optimize_context':
      return await optimizeContext(args, env);
      
    case 'get_session':
      return await getSession(args, env);
      
    default:
      throw new Error(`Unknown tool: ${name}`);
  }
}

// ============================================================================
// YOUR EXISTING SOPHISTICATED FUNCTIONALITY (KEPT INTACT)
// ============================================================================

async function queryContext(params, env) {
  const { query, maxTokens = 2048, sessionId = 'default' } = params;
  
  // Initialize engines
  const scoringEngine = new ContextScoringEngine({ adhdMode: true });
  const shedder = new IntelligentShedder({ maxTokens, adhdMode: true });
  
  // Get or create session
  const session = await getOrCreateSession(sessionId, env);
  
  // Generate embedding for query
  const queryEmbedding = await generateEmbedding(query, env);
  
  // Search for relevant segments
  const segments = await searchSegments(queryEmbedding, env);
  
  // Create session context for scoring
  const sessionContext = {
    sessionId,
    queryEmbedding,
    recentActivity: session.recentActivity || [],
    activeDomains: extractDomains(query),
    hyperfocusPeriods: session.hyperfocusPeriods || [],
    lastTopic: session.lastTopic
  };
  
  // Score segments
  const scoredSegments = segments.map(segment => ({
    ...segment,
    score: scoringEngine.calculateContextValue(segment, sessionContext)
  }));
  
  // Sort by score
  scoredSegments.sort((a, b) => b.score - a.score);
  
  // Apply shedding if needed
  const currentTokenCount = scoredSegments.reduce((sum, s) => sum + (s.tokenCount || 0), 0);
  
  let optimizedSegments = scoredSegments;
  if (currentTokenCount > maxTokens) {
    optimizedSegments = await shedder.shedContext(
      scoredSegments,
      currentTokenCount,
      scoringEngine,
      sessionContext
    );
  }
  
  // Update session
  await updateSession(sessionId, {
    lastQuery: query,
    lastTopic: extractTopic(query),
    lastActivity: Date.now()
  }, env);
  
  return {
    content: [
      {
        type: 'text',
        text: `Found ${optimizedSegments.length} relevant context segments for: "${query}"\n\n` +
              optimizedSegments.slice(0, 5).map(s => 
                `**${s.metadata?.topic || 'Context'}** (Score: ${s.score?.toFixed(3)})\n${s.content?.substring(0, 200)}...`
              ).join('\n\n')
      }
    ]
  };
}

async function storeSegment(params, env) {
  const { content, metadata = {}, sessionId = 'default' } = params;
  
  const segmentId = crypto.randomUUID();
  const embedding = await generateEmbedding(content, env);
  const tokenCount = Math.ceil(content.length / 4);
  
  const segment = {
    id: segmentId,
    content: content.substring(0, 2000), // Store more content
    embedding,
    metadata: {
      ...metadata,
      timestamp: Date.now(),
      sessionId,
      topic: extractTopic(content)
    },
    tokenCount,
    accessCount: 0
  };
  
  // Store in Sanctuary KV namespace
  await env.Sanctuary.put(
    `segment:${segmentId}`,
    JSON.stringify(segment),
    { expirationTtl: 86400 * 30 }
  );
  
  return {
    content: [
      {
        type: 'text',
        text: `✅ Successfully stored knowledge segment: "${segment.metadata.topic}" (${tokenCount} tokens)`
      }
    ]
  };
}

async function optimizeContext(params, env) {
  const { sessionId = 'default', targetTokens = 50000 } = params;
  
  const segments = await getSessionSegments(sessionId, env);
  const currentTokenCount = segments.reduce((sum, s) => sum + (s.tokenCount || 0), 0);
  
  const scoringEngine = new ContextScoringEngine({ adhdMode: true });
  const shedder = new IntelligentShedder({ maxTokens: targetTokens, adhdMode: true });
  
  const session = await getOrCreateSession(sessionId, env);
  const sessionContext = { sessionId, ...session };
  
  const optimized = await shedder.shedContext(
    segments,
    currentTokenCount,
    scoringEngine,
    sessionContext
  );
  
  const reduction = Math.round((1 - optimized.length / segments.length) * 100);
  
  return {
    content: [
      {
        type: 'text',
        text: `🧠 Context optimization complete!\n\n` +
              `**Before**: ${segments.length} segments, ${currentTokenCount} tokens\n` +
              `**After**: ${optimized.length} segments, ${optimized.reduce((sum, s) => sum + (s.tokenCount || 0), 0)} tokens\n` +
              `**Reduction**: ${reduction}% smaller with ADHD-aware prioritization`
      }
    ]
  };
}

async function getSession(params, env) {
  const { sessionId = 'default' } = params;
  const session = await getOrCreateSession(sessionId, env);
  
  return {
    content: [
      {
        type: 'text',
        text: `📊 Session: ${sessionId}\n\n` +
              `**Created**: ${new Date(session.created).toLocaleString()}\n` +
              `**Recent Activities**: ${session.recentActivity?.length || 0}\n` +
              `**ADHD Mode**: ${session.config?.adhdMode ? '✅ Enabled' : '❌ Disabled'}\n` +
              `**Hyperfocus Periods**: ${session.hyperfocusPeriods?.length || 0}`
      }
    ]
  };
}

// ============================================================================
// KEEP ALL YOUR EXISTING CLASSES AND HELPER FUNCTIONS
// ============================================================================

// Context Scoring Engine
class ContextScoringEngine {
  constructor(config = {}) {
    this.config = {
      weights: {
        recency: 0.25,
        relevance: 0.35,
        uniqueness: 0.15,
        compressibility: 0.10,
        networkEffect: 0.15
      },
      recencyDecay: 86400000,
      adhdMode: config.adhdMode || false
    };
  }
  
  calculateContextValue(segment, sessionContext) {
    const scores = {
      recency: this.calculateRecencyScore(segment),
      relevance: this.calculateRelevanceScore(segment, sessionContext),
      uniqueness: Math.min(1, 1 / Math.log2((segment.accessCount || 0) + 2)),
      compressibility: segment.compressionRatio || 0.5,
      networkEffect: Math.min(1, ((segment.inboundLinks?.length || 0) + 
                                  (segment.outboundLinks?.length || 0)) / 10)
    };
    
    if (this.config.adhdMode && segment.metadata?.tags?.includes('prodigy_moment')) {
      Object.keys(scores).forEach(key => scores[key] *= 1.3);
    }
    
    let total = 0;
    for (const [key, value] of Object.entries(scores)) {
      total += value * this.config.weights[key];
    }
    
    return total;
  }
  
  calculateRecencyScore(segment) {
    const age = Date.now() - (segment.metadata?.timestamp || segment.timestamp || 0);
    return Math.exp(-age / this.config.recencyDecay);
  }
  
  calculateRelevanceScore(segment, sessionContext) {
    if (!segment.embedding || !sessionContext.queryEmbedding) return 0.5;
    
    let dotProduct = 0;
    for (let i = 0; i < Math.min(segment.embedding.length, sessionContext.queryEmbedding.length); i++) {
      dotProduct += segment.embedding[i] * sessionContext.queryEmbedding[i];
    }
    
    return Math.min(1, Math.abs(dotProduct));
  }
}

// Intelligent Shedder
class IntelligentShedder {
  constructor(options = {}) {
    this.maxTokens = options.maxTokens || 128000;
    this.targetUtilization = 0.8;
    this.strategy = options.strategy || 'adaptive';
    this.adhdMode = options.adhdMode || false;
  }
  
  async shedContext(segments, currentTokenCount, scoringEngine, sessionContext) {
    const targetTokens = this.maxTokens * this.targetUtilization;
    
    if (currentTokenCount <= targetTokens) {
      return segments;
    }
    
    const scored = segments.map(s => ({
      ...s,
      priority: s.score * (s.metadata?.critical ? 10 : 1) * 
                (this.adhdMode && s.metadata?.tags?.includes('prodigy_moment') ? 2 : 1)
    }));
    
    scored.sort((a, b) => b.priority - a.priority);
    
    const retained = [];
    let tokenSum = 0;
    
    for (const segment of scored) {
      if (tokenSum + (segment.tokenCount || 0) <= targetTokens) {
        retained.push(segment);
        tokenSum += segment.tokenCount || 0;
      } else if (segment.metadata?.critical) {
        retained.push(segment);
        tokenSum += segment.tokenCount || 0;
      }
    }
    
    return retained;
  }
}

// All your existing helper functions...
async function generateEmbedding(text, env) {
  if (env.AI) {
    try {
      const response = await env.AI.run('@cf/baai/bge-base-en-v1.5', {
        text: text.substring(0, 512)
      });
      return response.data[0];
    } catch (e) {
      console.error('AI embedding failed:', e);
    }
  }
  
  const hash = await crypto.subtle.digest('SHA-256', new TextEncoder().encode(text));
  const array = new Float32Array(hash);
  return Array.from(array).slice(0, 384);
}

async function searchSegments(embedding, env) {
  const segments = [];
  
  try {
    const list = await env.Sanctuary.list({ 
      prefix: 'segment:', 
      limit: 100 
    });
    
    for (const key of list.keys.slice(0, 20)) {
      const data = await env.Sanctuary.get(key.name);
      if (data) {
        segments.push(JSON.parse(data));
      }
    }
  } catch (e) {
    console.error('Search failed:', e);
  }
  
  return segments;
}

async function getOrCreateSession(sessionId, env) {
  const key = `session:${sessionId}`;
  const existing = await env.Sanctuary.get(key);
  
  if (existing) {
    return JSON.parse(existing);
  }
  
  const session = {
    id: sessionId,
    created: Date.now(),
    config: {
      weights: {
        recency: 0.25,
        relevance: 0.35,
        uniqueness: 0.15,
        compressibility: 0.10,
        networkEffect: 0.15
      },
      adhdMode: true
    },
    recentActivity: [],
    hyperfocusPeriods: [],
    segments: []
  };
  
  await env.Sanctuary.put(key, JSON.stringify(session), {
    expirationTtl: 86400 * 7
  });
  
  return session;
}

async function updateSession(sessionId, updates, env) {
  const session = await getOrCreateSession(sessionId, env);
  
  Object.assign(session, updates);
  
  if (updates.lastQuery) {
    session.recentActivity = session.recentActivity || [];
    session.recentActivity.push({
      type: 'query',
      topic: updates.lastTopic,
      timestamp: Date.now()
    });
    
    if (session.recentActivity.length > 50) {
      session.recentActivity = session.recentActivity.slice(-50);
    }
  }
  
  await env.Sanctuary.put(
    `session:${sessionId}`,
    JSON.stringify(session),
    { expirationTtl: 86400 * 7 }
  );
}

async function getSessionSegments(sessionId, env) {
  const segments = [];
  
  try {
    const list = await env.Sanctuary.list({
      prefix: 'segment:',
      limit: 100
    });
    
    for (const key of list.keys) {
      const data = await env.Sanctuary.get(key.name);
      if (data) {
        const segment = JSON.parse(data);
        if (segment.metadata?.sessionId === sessionId) {
          segments.push(segment);
        }
      }
    }
  } catch (e) {
    console.error('Get segments failed:', e);
  }
  
  return segments;
}

function extractTopic(text) {
  const words = text.toLowerCase().split(/\s+/);
  const stopWords = new Set(['the', 'a', 'an', 'and', 'or', 'but', 'in', 'on', 'at']);
  const keywords = words.filter(w => !stopWords.has(w) && w.length > 3).slice(0, 3);
  return keywords.join('-') || 'general';
}

function extractDomains(text) {
  const domains = [];
  const patterns = {
    tech: /\b(code|api|database|cloud|server)\b/gi,
    business: /\b(strategy|market|revenue|customer|brand)\b/gi,
    creative: /\b(design|creative|inspiration|art|music)\b/gi
  };
  
  for (const [domain, pattern] of Object.entries(patterns)) {
    if (pattern.test(text)) {
      domains.push(domain);
    }
  }
  
  return domains.length > 0 ? domains : ['general'];
}
```
## Required Cloudflare Settings:
### KV Namespace Bindings:
- **Sanctuary** → Variable name: `Sanctuary`
- **Secrets** → Variable name: `Secrets` (optional)

### Environment Variables:
- `MAX_CONTEXT_TOKENS` = `128000`
- `ADHD_MODE_ENABLED` = `true`
- `DEFAULT_SHEDDING_STRATEGY` = `adaptive`

## Testing Your Fixed Worker:
```bash
# Test initialize (this was failing before)
curl -X POST https://knowledge-hub-mcp.harveytagalicud7.workers.dev/mcp \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "initialize",
    "params": {
      "protocolVersion": "2025-06-18",
      "capabilities": {},
      "clientInfo": {"name": "claude-desktop", "version": "1.0.0"}
    },
    "id": 1
  }'

# Should return: {"jsonrpc":"2.0","result":{"protocolVersion":"2025-06-18",...},"id":1}
```
## Key Changes Made:
✅ **Added Missing MCP Methods**:
- `initialize` - Now responds correctly to Claude's handshake
- `tools/list` - Lists your sophisticated tools
- `tools/call` - Routes to your existing functions

✅ **Fixed Response Format**:
- Proper JSON-RPC 2.0 format
- Correct MCP tool result structure

✅ **Kept Your Functionality**:
- All your sophisticated ADHD-aware context engine
- Intelligent shedding algorithms
- Advanced scoring engine
- Everything now accessible via proper MCP tools

## Deploy Instructions:
1. Go to Cloudflare Dashboard → Workers & Pages
2. Click on your `knowledge-hub-mcp` worker
3. Click "Quick Edit"
4. Replace ALL code with the fixed version above
5. Click "Save and Deploy"
6. Restart Claude Desktop

**Your Worker will now connect properly!** 🎉