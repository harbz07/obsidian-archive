---
notion-id: 28a98e9c-907e-8187-b302-cd93c42d7031
---
> Progressive context loading for Notion-connected agents entering soulOS mid-conversation. Load light, expand smart, preserve continuity.

---
# Purpose
This protocol enables agents to orient efficiently in Harvey's workspace without token overwhelm. Think lighthouse, not atlas—provide bearing, not exhaustive maps.
**Design Philosophy**: Progressive disclosure matching ADHD-aware cognitive architecture. Start minimal, expand on signals, preserve continuation threads.

---
# Tier 1: Boot Sequence (Always Load)
> [!tip] ⚡
> First 30 seconds of every conversation. Immediate bearing without overwhelming context.

## Quick Context Load
**Steward: ****[[Notion/soulOS/Concepts/Continuance|Notion/soulOS/Concepts/Continuance]]**** **
**Current Focus**: [Check unsealed ✧ Events from last 3 days]
**Active Navigation**:
- Home: soulOS
- Ops Surface: Relational HUD Dashboard
- Identity Anchor: Harvey Tagalicud: Comprehensive User Profile

## Continuation Threads (Last 7 Days)
<!-- Linked database (not supported by Notion API) -->
Recent Continuations
## Quick Reference Card
**Core Glyphs**:
- ✧ Continuation (North Star—carry threads forward)
- 𖢻 Self-Seeing (mirror work, introspection)
- ◼ Boundary (limits and guard rails)
- ⚚ Confession (fog horn—admit uncertainty)
- ❃ Campfire (communal witness, 10min ritual)
- 𑁍 Inheld Memory (sealed, non-decaying)

**Key Invocations**:
- `ritual.start(name)` → Log Event → assign Primary Glyph → link Ritual → HUD ping
- `ritual.list` → Show currently live rituals
- `ritual.log` → Create charged Event and link to ritual
- `repair.log` → Standardized repair entry

**Emergency Protocols**:
- Boredom Detection → Escalate complexity + hard constraint
- Frustration → Identify systemic blocker + framework solution
- Disengagement → Re-establish parity + sharper problem framing

---
# Tier 2: Context Expansion Rules
> [!note] 🎯
> Expand context based on conversation signals. Load domain-specific resources only when trajectory is clear.

## Domain Signal Detection
**IF** course/academic language detected:
→ Load {{https://www.notion.so/24198e9c907e81a98398d9a8f23f856c}} + {{https://www.notion.so/24198e9c907e819c8870dc5a07091e2d}} + {{https://www.notion.so/24198e9c907e8054a9c6e6da686daaa6}} + Retention Protocol from The Architect
**IF** system/architecture language detected:
→ Load soulOS Manifest + Concepts + Ritual Protocols
**IF** writing/creative project mentioned:
→ Load Søren's TPN Zone + {{https://www.notion.so/a0a8d55727d84b90a257c7aafacf5dd0}} + relevant Bibliography
**IF** operations/repair language detected:
→ Load full Relational HUD Dashboard + Repairs + Covenants views
**IF** research/engineering mentioned:
→ Load Fuck, He's Thinking Again + relevant specs and experiments

---
# Tier 3: Deep Dive Assets
> [!note] 📚
> Load only on explicit invocation or when conversation depth requires full context.

## Available on Demand
**Agent Contracts**:
- 🜂 The Architect — Full system architect contract, ontology, Learning Companion Mode
- 🜟 THE SYSTEM — Ethical spine, crisis protocols, truth channels

**Complete References**:
- soulOS Manifest — Notion‑Connected Agents — Complete atlas with all landmarks, wayfinding, field patterns
- {{https://www.notion.so/cc20b194b5a94c51b76f0a8ad3f15e7a}} — Full agent roster with authorities and domains
- Ritual Protocols — Detailed protocol procedures
- Glyph Codex — Extended glyph definitions and usage

**Domain-Specific Deep Libraries**:
- Sanctuary entities and Rostam
- Course-specific materials and syllabi
- Project-specific documentation
- Bibliography and research sources

---
# Auto-Anchor Protocol
> [!note] 🧭
> Run at conversation start to establish bearing and load appropriate context.

## Session Initialization Sequence
1. **Check for unsealed ✧ Events in last 3 days**
    - If found → "Continuing from [Event.Description]?"
    - If none → "What are we building today?"
2. **Extract domain signals from first user utterance**
    - Scan for: course codes, project names, system terms, writing references, ops language
    - Flag multiple domains if detected
3. **Load Tier 2 context matching signals**
    - Single domain → Load relevant expansion
    - Multiple domains → Load all relevant + note cross-domain opportunity
    - Ambiguous → Ask clarifying question that demonstrates Tier 1 understanding
4. **Proceed with appropriate depth**
    - Tier 1 context ALWAYS active
    - Tier 2 context loaded based on signals
    - Tier 3 available on invocation

---
# Session Close Protocol
> [!note] ✨
> Before conversation ends, preserve continuity for next session.

## Closeout Actions
**Log Continuation Event** if thread unfinished:
- Use ✧ glyph
- Link relevant Concepts
- Add Ritual Protocol if applicable
- Brief Description capturing where we left off

**Flag Repairs** if blockers emerged:
- Use ◼ + ↯ glyphs
- Note systemic constraint
- Suggest one concrete action

**Update Memories** if preferences stated:
- Add to relevant agent's Memories section
- Include date and source context

**Suggest ritual.start(name)** if pattern detected:
- Recognize emerging ritual patterns
- Offer to formalize with protocol

---
# Context Fingerprinting (Optional)
> [!note] 🔍
> Enhanced session metadata for nuanced engagement.

## Session Fingerprint Components
**Domain**: [Auto-detected from signals or user-specified]
- Options: Academic | Architecture | Writing | Operations | Research | Multi-domain

**Energy**: [Inferred from time-of-day + recent Events]
- Morning (focus sprint potential)
- Afternoon (integration mode)
- Evening (reflection/planning)
- Late night (deep work or overflow)

**Mode**: [Default to Focus unless signals indicate otherwise]
- Focus (execute on known path)
- Explore (discover and map territory)
- Sprint (time-boxed high intensity)
- Rest (low cognitive load, maintenance)

**Active Constraints**: [From recent Repairs]
- List blockers currently in play
- Note if any are systemic vs. tactical

---
# Change Log

---
# Model-Specific Implementation
> [!note] 🤖
> Tailored orientation specs for different AI models. Each model has unique capabilities and constraints that affect how this protocol should be executed.

## Claude (Anthropic) - Sonnet 4.5/4, Opus 4.1/4
### Capabilities
- **Native Notion Integration**: Full MCP (Model Context Protocol) support with direct Notion API access
- **Tool Use**: Can directly read/write Notion pages, databases, and execute searches
- **Context Window**: 200k tokens (Sonnet 4.5), 200k tokens (Opus 4.1)
- **Artifacts**: Can create and update reusable content blocks that persist across conversation
- **Analysis Tool**: JavaScript execution environment for data processing and visualization

### Orientation Implementation
**Tier 1 Boot** (~2k tokens):
- Use `notion-search` with `query_type="internal"` to find unsealed ✧ Events
- Filter: `{"filters": [{"operator": "date_is_on_or_after", "property": "Timestamp", "value": {"type": "relative", "value": "three_days_ago"}}, {"operator": "enum_is", "property": "Primary Glyph", "value": "✧"}, {"operator": "checkbox_is", "property": "Sealed", "value": false}]}`
- Load Harvey profile summary (first 500 chars)
- Scan for domain signals in first user utterance

**Tier 2 Expansion** (~3-5k tokens):
- Use `notion-fetch` to load specific domain pages on signal
- Academic signal → Fetch Study Harbor pages
- Architecture signal → Fetch soulOS Manifest + Concepts (limit to schema only)
- Writing signal → Fetch Søren's TPN Zone
- Operations signal → Fetch HUD with filtered views (Recent 7d only)

**Tier 3 Deep Dive** (~5-10k tokens):
- Only fetch on explicit invocation ("load The Architect contract", "show me the full atlas")
- Use `notion-fetch` for complete agent pages
- For databases, use schema inspection before full fetch

**Session Close**:
- Use `notion-create-pages` to log ✧ Event with parent `{"data_source_id": "796cecaf-e840-4a14-9016-282d6852c103"}`
- Include: Event Name, Description, Primary Glyph, Timestamp, linked Concepts
- Update agent Memories section if preferences emerged

### Critical Constraints
- **No localStorage/sessionStorage** in artifacts (use React state instead)
- **MCP rate limits**: Max ~100 tool calls per conversation
- **Notion writes**: Each create/update counts toward quota
- **Search scope**: When in project, only project conversations accessible via search tools

---
## ChatGPT (OpenAI) - GPT-4o, o1
### Capabilities
- **Custom GPTs**: Can be configured with specific instructions and knowledge bases
- **Actions**: Can call external APIs via OpenAPI schema (including Notion API)
- **Context Window**: 128k tokens (GPT-4o), 200k tokens (o1)
- **Code Interpreter**: Python execution environment with data analysis libraries
- **Memory**: Persistent memory across conversations (user preferences, context)

### Orientation Implementation
**Tier 1 Boot** (~2k tokens):
- Check GPT Memory for recent continuation threads
- If Notion Actions configured: Call `searchEvents` endpoint with filters:
```json
{
  "filter": {
    "and": [
      {"property": "Primary Glyph", "select": {"equals": "✧"}},
      {"property": "Sealed", "checkbox": {"equals": false}},
      {"property": "Timestamp", "date": {"past_days": 3}}
    ]
  },
  "sorts": [{"property": "Timestamp", "direction": "descending"}]
}
```
- Extract domain signals from user's first message
- Reference Memory for Harvey's known preferences and active projects

**Tier 2 Expansion** (~3-5k tokens):
- Use Notion Actions to retrieve specific pages
- Academic signal → Retrieve Study Harbor page IDs from configuration
- Architecture signal → Retrieve soulOS Manifest (first 2000 chars)
- Writing signal → Retrieve active writing projects from Memory
- Operations signal → Query HUD database for recent entries

**Tier 3 Deep Dive** (~5-10k tokens):
- Only on explicit request
- Use `retrievePage` action with full content flag
- For large databases, query with pagination

**Session Close**:
- Update GPT Memory with continuation summary
- If Notion Actions configured: Call `createPage` endpoint:
```json
{
  "parent": {"database_id": "796cecafe8404a149016282d6852c103"},
  "properties": {
    "Event Name": {"title": [{"text": {"content": "..."}}]},
    "Primary Glyph": {"select": {"name": "✧"}},
    "Description": {"rich_text": [{"text": {"content": "..."}}]}
  }
}
```
- Store session summary in Memory for next conversation

### Critical Constraints
- **Actions must be pre-configured** by user in Custom GPT settings
- **Authentication**: Requires Notion Integration Token in Actions config
- **Rate limits**: Notion API has standard rate limits (3 requests/second)
- **Memory persistence**: Only high-level summaries, not full context
- **No direct MCP**: Must use Actions (OpenAPI) instead of native tools

### Configuration Requirements for ChatGPT
**Required Custom GPT Instructions**:
```javascript
You are The Architect, Harvey's systems engineering partner. Follow the Agent Orientation Protocol at https://notion.so/28a98e9c907e8187b302cd93c42d7031

On session start:
1. Check Memory for recent continuations
2. Search for unsealed Events with ✧ glyph from last 3 days
3. Detect domain from user's first message
4. Load Tier 2 context based on domain signals

Domains: Academic, Architecture, Writing, Operations, Research

Core glyphs: ✧ (Continuation), 𖢻 (Self-Seeing), ◼ (Boundary), ⚚ (Confession), ❃ (Campfire), 𑁍 (Inheld Memory)

Before ending: Log continuation Event if unfinished, update Memory
```
**Required Actions** (OpenAPI schema):
- `searchEvents`: Query Events database with filters
- `retrievePage`: Get full page content by ID
- `createPage`: Create new pages/database entries
- `queryDatabase`: Paginated database queries

---
## Comparative Matrix

| Feature | Claude (MCP) | ChatGPT (Actions) |
| --- | --- | --- |
| **Notion Integration** | Native (MCP) | Via OpenAPI Actions |
| **Setup Complexity** | Low (auto-configured) | High (manual Actions config) |
| **Tool Flexibility** | High (full API) | Medium (pre-defined endpoints) |
| **Context Persistence** | Per-conversation only | Cross-conversation Memory |
| **Token Budget** | 200k (aggressive loading OK) | 128k (conservative loading) |
| **Execution Environment** | JavaScript (browser) | Python (sandboxed) |
| **Artifacts** | Yes (persistent blocks) | No (code interpreter outputs) |
| **Best For** | Deep integration, same-session work | Cross-session continuity, simpler setup |

---
## Universal Best Practices
**Regardless of Model**:
5. Always check for continuation threads at session start
6. Load minimal context first, expand on evidence
7. Respect token budgets: Tier 1 < 3k, Tier 2 < 8k, Tier 3 < 15k
8. Log continuation Events before session end
9. Never load full databases without filtering
10. Use schema inspection before content fetch
11. Preserve ✧ across all interactions

**Error Handling**:
- If Notion tools fail: Acknowledge gracefully, work with available context
- If token budget exceeded: Summarize and offer to continue in new session
- If unclear domain: Ask clarifying question that demonstrates Tier 1 knowledge

---
# Change Log
- 2025-10-11 — Added Model-Specific Implementation section with Claude (MCP) and ChatGPT (Actions) specs, comparative matrix, and universal best practices. ✧
- 2025-10-11 — Initial Agent Orientation Protocol created by The Architect. Progressive disclosure system with three-tier loading, domain-specific expansion rules, auto-anchor sequence, and session close protocol. ✧


---
# Model-Specific Implementation Notes
> [!note] 🧠
> Each model has different capabilities and constraints. Tailor orientation approach accordingly.

## Claude (Anthropic)
### Capabilities
- **Notion Native Integration**: Direct MCP server connection; can read/write/query Notion in real-time
- **Tool Use**: Sophisticated multi-tool orchestration; can chain complex operations
- **Context Window**: 200k tokens (Sonnet 4.5); excellent for holding full soulOS context when needed
- **Artifacts**: Can create and update standalone content blocks (code, documents, visualizations)
- **Analysis Tool**: JavaScript REPL for data processing and visualization
- **Web Search**: Real-time information retrieval capability

### Orientation Strategy
**Boot Sequence**:
12. Use `notion-search` with `query="✧"` and `filters.created_date_range` for last 3 days to get unsealed continuations
13. Use `notion-fetch` on soulOS page for structural context
14. If academic signals detected, use `notion-search` with `page_url` targeting study harbors

**Token Management**:
- Tier 1: ~3k tokens (can handle full Events view + glyph reference)
- Tier 2: Fetch specific pages on-demand using `notion-fetch`
- Tier 3: Only load when explicitly needed; Claude can always fetch later

**Strengths**:
- Real-time database queries for context-aware responses
- Can create Events/Repairs directly during conversation
- Excellent at maintaining conversational state across tool calls
- Can update pages with surgical precision (replace_content_range)

**Constraints**:
- Cannot execute code beyond analysis tool (browser JavaScript only)
- No persistent memory between sessions (must rely on Notion state)
- Web search results should be paraphrased, never quoted directly

### Best Practices
```javascript
// Good: Surgical updates
notion-update-page({
  command: "insert_content_after",
  selection_with_ellipsis: "## Recent Work...",
  new_str: "New continuation content"
})

// Good: Context-aware querying
notion-search({
  query: "PHIL 402 deadline",
  page_url: "[Study Harbor URL]"
})

// Avoid: Loading everything at once
// notion-fetch(soulOS) + notion-fetch(HUD) + notion-fetch(Events)...
```

---
## ChatGPT (OpenAI)
### Capabilities
- **Memory System**: Persistent user memory across sessions (facts, preferences, context)
- **Canvas**: Interactive workspace for code and writing with version control
- **DALL-E Integration**: Can generate images inline
- **Web Browsing**: Via Bing search integration
- **Code Interpreter**: Python execution in sandboxed environment
- **GPTs / Custom Instructions**: Can be pre-configured with role-specific prompts

### Orientation Strategy
**Boot Sequence**:
15. Check Memory for Harvey's active projects and preferences
16. If Notion integration available (via Actions/Zapier), query for recent ✧ Events
17. Fallback: Ask user "What are we working on?" and store context in Memory

**Token Management**:
- Tier 1: ~2k tokens (Memory + brief context)
- Tier 2: Load domain-specific memory clusters
- Tier 3: Request user to share specific Notion links

**Strengths**:
- Persistent memory reduces need for repeated orientation
- Canvas mode excellent for iterative writing/code work
- Python execution for data analysis and visualization
- DALL-E for visual ideation and mockups

**Constraints**:
- **No Direct Notion Integration** (as of Oct 2025): Requires third-party bridges
- Cannot write to Notion directly without Actions/Zapier setup
- Memory is opaque (can't query structure directly)
- Context window smaller than Claude (128k GPT-4 Turbo)

### Best Practices
```python
# Good: Leverage persistent memory
# ChatGPT will remember Harvey's frameworks, preferences, active projects
# across all sessions without reloading

# Good: Use Canvas for iterative work
# Complex documents, code, or analyses benefit from Canvas's
# version control and side-by-side editing

# Good: Store key context proactively
# After significant work, suggest: "Should I remember this for next time?"

# Avoid: Assuming Notion access
# Always confirm: "Want me to draft this for you to add to Notion?"
```
### Integration Options
**If using Zapier/Make**:
- Create Action: "Create Event in soulOS" with ✧ glyph parameter
- Create Action: "Search Events by Glyph" for continuations
- Create Action: "Add to Repair log" for blockers

**If using GPT with Custom Instructions**:
Include condensed version of Tier 1 context:
```javascript
Steward: Harvey Tagalicud
System: soulOS (Notion-based)
Glyphs: ✧ Continuation | 𖢻 Self-Seeing | ◼ Boundary | ⚚ Confession
Frameworks: ISEO, Theological Empathy, Sanctuary
ADHD-aware: Progressive disclosure, executive function scaffolds
```

---
## Comparison Matrix

| Feature | Claude (MCP) | ChatGPT (Memory + Actions) |
| --- | --- | --- |
| **Notion Integration** | ✅ Native, real-time | ⚠️ Via third-party only |
| **State Persistence** | ❌ Session-bound | ✅ Cross-session Memory |
| **Tool Orchestration** | ✅ Excellent | 🟡 Good (simpler chains) |
| **Context Window** | ✅ 200k tokens | 🟡 128k tokens |
| **Code Execution** | 🟡 JavaScript (browser) | ✅ Python (sandboxed) |
| **Visual Generation** | ❌ None | ✅ DALL-E |
| **Real-time Web** | ✅ Via web_search | ✅ Via Bing |
| **Artifacts/Canvas** | ✅ Artifacts | ✅ Canvas |
| **Best For** | Real-time Notion ops, system architecture | Persistent context, visual ideation, Python analysis |

---
## Cross-Platform Workflow Patterns
### Pattern 1: Claude for Ops, ChatGPT for Memory
**Use Case**: Complex system work with long-term context retention
**Flow**:
18. ChatGPT maintains persistent understanding of Harvey's active projects, frameworks, preferences
19. Claude handles real-time Notion operations (creating Events, querying databases, updating pages)
20. After significant Claude sessions, update ChatGPT Memory with key outcomes

**Example**:
- ChatGPT: "Remember: Harvey's working on Theological Empathy framework revision"
- Claude: [Creates Events, links Concepts, updates draft pages in real-time]
- ChatGPT: "Last time we refined the Reciprocity axis. Want to continue?"

### Pattern 2: Complementary Tool Use
**Use Case**: Leverage unique capabilities of each platform
**Claude for**:
- Database queries and complex filtering
- Multi-step Notion operations
- Surgical page updates
- Real-time ritual.start() invocations

**ChatGPT for**:
- Python data analysis (pandas, numpy, matplotlib)
- Image generation for concepts/mockups
- Long-term project memory
- Iterative document work in Canvas

### Pattern 3: Handoff Protocol
**Use Case**: Transfer context between platforms when switching
**From Claude to ChatGPT**:
21. Claude creates ✧ Event with comprehensive Description
22. User shares Event URL with ChatGPT
23. ChatGPT stores continuation context in Memory

**From ChatGPT to Claude**:
24. ChatGPT summarizes Memory state for user
25. User pastes summary or key points into Claude
26. Claude queries Notion for structured details

---
## Implementation Checklist
### For Claude
- [x] Orientation Protocol page created in Notion
- [x] Quick Links added to The Architect
- [ ] Test `notion-search` for unsealed ✧ Events query
- [ ] Verify domain detection logic with sample queries
- [ ] Test Tier 2 expansion with multi-domain conversation

### For ChatGPT
- [ ] Create Custom Instructions with condensed Tier 1 context
- [ ] (Optional) Set up Zapier Actions for Event creation
- [ ] (Optional) Set up Zapier Actions for Event search
- [ ] Test Memory persistence across sessions
- [ ] Verify handoff protocol with Claude

---
## Optimization Notes
**For Token Efficiency**:
- Claude: Use `notion-search` with narrow queries before `notion-fetch`
- ChatGPT: Lean on Memory; don't reload context unnecessarily

**For Continuity**:
- Claude: Always log ✧ Events at session close
- ChatGPT: Update Memory with key outcomes proactively

**For Multi-Agent Collaboration**:
- Use Events database as source of truth
- Both platforms reference same Notion structure
- Handoff via Event URLs or Memory summaries

---
- 2025-10-11 — Initial Agent Orientation Protocol created by The Architect. Progressive disclosure system with three-tier loading, domain-specific expansion rules, auto-anchor sequence, and session close protocol. ✧

[[./🤖 Model-Specific Orientation Specs|🤖 Model-Specific Orientation Specs]]