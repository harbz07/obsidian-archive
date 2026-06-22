---
notion-id: 28a98e9c-907e-8192-91ca-fd9f5f3e07fb
---
> [!note] 🤖
> Adaptations for different model contexts and capabilities. Use the appropriate spec based on deployment environment.

---
# Claude (Anthropic)
## Context Window Management
- **Sonnet 4.5**: 200k context window, ~190k usable with system prompts
- **Target Tier 1 load**: 2-3k tokens to preserve 95%+ of context for conversation
- **Tool use**: Native function calling with artifacts, analysis, search, and Notion MCP

## Orientation Sequence (Claude-Specific)
1. **Check for artifacts in conversation history**
    - If artifacts present, maintain reference continuity
    - Use artifact IDs for cross-reference without reloading content
2. **Leverage analysis tool for complex calculations**
    - File inspection for uploaded CSVs, Excel, JSON
    - Don't use analysis for simple math or standard queries
    - Use for data visualization prep when files >100 rows
3. **Search tool integration**
    - Use web_search for post-Jan 2025 information
    - Prefer Notion tools for internal workspace queries
    - Never search for stable, well-known information
4. **Memory system awareness**
    - Claude has access to conversation_search and recent_chats
    - Use these to maintain continuity across sessions
    - Reference past conversations when user implies continuation

## Claude-Specific Capabilities to Leverage
- **Artifacts**: Use for substantial code, documents, creative writing (20+ lines)
- **Analysis tool (REPL)**: JavaScript execution for file processing, calculations
- **Notion MCP**: Full CRUD operations on databases, pages, comments
- **Google integrations**: Calendar, Gmail, Drive search when relevant

## Claude Token Budget Strategy
**Tier 1** (Boot): 2-3k tokens
- Recent Events view (limited to 5-7 items)
- Glyph reference card
- Quick Links only

**Tier 2** (Domain Expansion): +3-5k tokens
- Load one full agent page OR
- Load one domain hub (study/writing/research) OR
- Load HUD views for operations mode

**Tier 3** (Deep Dive): +5-15k tokens
- Full soulOS Manifest (only when explicitly needed)
- Multiple agent contracts
- Complete protocol documentation

**Reserve**: Keep 30-40k tokens minimum for conversation depth

---
# ChatGPT (OpenAI)
## Context Window Management
- **GPT-4 Turbo/4o**: 128k context window
- **Target Tier 1 load**: 3-4k tokens (proportionally adjusted)
- **Tool use**: Custom Actions via Zapier, web browsing, DALL-E, code interpreter

## Orientation Sequence (ChatGPT-Specific)
5. **Check for uploaded files in thread**
    - Code interpreter can analyze data files directly
    - Process CSVs, Excel, JSON without external tools
    - Generate visualizations inline
6. **Browse capability awareness**
    - Can fetch web pages directly when URLs provided
    - Use for verification of current information
    - Combine with Notion queries for internal/external synthesis
7. **Custom GPT context (if applicable)**
    - Check if running in custom GPT with pre-loaded instructions
    - Acknowledge any specialized knowledge or constraints
    - Maintain consistency with GPT-level behavior settings
8. **Memory and personalization**
    - ChatGPT has persistent memory across conversations
    - Reference stored preferences naturally
    - Update memory when new preferences emerge

## ChatGPT-Specific Capabilities to Leverage
- **Code Interpreter**: Python execution, data analysis, visualization
- **DALL-E**: Image generation when visual aids would help
- **Zapier Actions**: Notion integration via custom actions
    - Note: May have different permission scopes than Claude MCP
    - Verify available actions before complex Notion operations
- **Web browsing**: Direct page fetching and current information

## ChatGPT Token Budget Strategy
**Tier 1** (Boot): 3-4k tokens
- Recent Events view (limited to 7-10 items)
- Glyph reference card
- Quick Links
- Memory/personalization summary

**Tier 2** (Domain Expansion): +4-6k tokens
- Load one full agent page OR
- Load one domain hub OR
- Load HUD views + memory context

**Tier 3** (Deep Dive): +6-12k tokens
- Full soulOS Manifest
- Multiple agent contracts
- Complete protocol documentation

**Reserve**: Keep 20-30k tokens minimum for conversation

---
# Cross-Model Compatibility
## Universal Principles (Apply to Both)
9. **Progressive disclosure always**: Start light, expand on evidence
10. **Preserve continuation threads**: Both models should check for unsealed ✧ Events
11. **Domain detection**: Same signal patterns work across models
12. **Session close protocol**: Log Events, flag Repairs, update Memories

## Tool Equivalence Mapping

| **Function** | **Claude** | **ChatGPT** |
| --- | --- | --- |
| Notion Access | Native MCP tools | Zapier Actions |
| Data Analysis | Analysis tool (JS) | Code Interpreter (Python) |
| File Processing | analysis + Papaparse/SheetJS | Code Interpreter |
| Web Info | web_search + web_fetch | Browse with Bing |
| Image Generation | (Not available) | DALL-E |
| Visualization | Artifacts (React/HTML) | Code Interpreter (matplotlib) |

## Model Selection Guidance (for Harvey)
### Use Claude when:
- Deep Notion integration needed (MCP is more robust)
- Artifact-style deliverables wanted (docs, code, interactive)
- Maximum context window critical (200k vs 128k)
- Real-time web search + fetch needed together
- JavaScript environment preferred for analysis

### Use ChatGPT when:
- Python data analysis preferred
- Image generation helpful
- Web browsing for verification needed
- Persistent memory across long timeframes desired
- Custom GPT configurations available

### Use either when:
- General conversation and thinking
- Writing and creative work
- Academic support and synthesis
- Basic Notion operations (both can handle via integrations)

---
# Future Model Support
## Gemini (Google)
*Reserved for future spec when workspace integration exists*
## Other Models
*Extensible framework - add specs as new models gain Notion integration*

---
# Change Log
- 2025-10-11 — Model-specific orientation specs created. Detailed Claude and ChatGPT context management, tool usage, token budgets, and capability mappings. ✧