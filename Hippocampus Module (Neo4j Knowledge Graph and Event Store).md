### Neo4j's Role as the Hippocampus Module in Cerebral SDK

In the Cerebral SDK project, Neo4j functions as the **Hippocampus Module**, crucial for managing episodic memory storage, relational indexing, and temporal continuity. This module is distinct from the Thalamus Module, which focuses on intake and scoring, by emphasizing structured, agent-relative episodes. The Hippocampus Module is responsible for storing Events and related structures, facilitating agent reminiscence and relational navigation.

### Key Blocks Enabling Processes

1. ==**Who Block (Participants and Targets)**==
   - ==Encodes relationality, identifying who is involved or affected in an event.==
   - ==Utilizes Cypher patterns to map participants and considered targets, ensuring the agent's ID is always included for self-relationality.==

==Memory | participant-map:==
   ```cypher
   FOREACH (name IN ev.who |
     MERGE (person:Person {name: name})
     MERGE (person)-[:PARTICIPATED_IN]->(e)
   )
   ```

==Reflection | relation-consider:==
   ```cypher
   OPTIONAL MATCH (e)-[:HAD_EFFECT_ON]->(f:Effect)-[:WITH_RESPECT_TO]->(t:Target)
   WHERE t.id = aid OR t.id IN r.considered_targets
   ```

2. **Why Block (Catalysts and Reasons)**
   - Captures motivations and tensions as `:Catalyst` nodes, allowing for reusable and multi-faceted episodes.

   Cypher for motivations:
   ```cypher
   FOREACH (reason IN ev.why |
     MERGE (c:Catalyst {description: reason})
     MERGE (e)-[:CATALYZED_BY]->(c)
   )
   ```

### Integration with Cerebral SDK

The Hippocampus Module integrates through a two-step process:
- **Thalamus Module**: Creates `:Capture` nodes, representing intake with scores.
- **Episodicization**: Transforms captures into `:Event` nodes, incorporating Who/Why blocks and Effects/Reflections for relational exploration.

This integration supports the biomimetic core of the Cerebral SDK, ensuring stable personality, temporal coherence, and agent partnership, while maintaining a clear distinction between intake and episodic hubs.

## Current Schema Recap

Based on our iterations, the schema we've converged on for the Hippocampus Module (Neo4j) is biomimetic episodic memory: `:Capture` for thalamic intake (raw, scored events), `:Event` as relational hubs (with Who, Why, Effects blocks), and `:Reflection` for agent-specific slices (prioritizing who_context for relationality). This supports free agent generation while grounding in shared objectivity, with Thalamus scoring handling significance but not reflections (processed in Prefrontal Cache). No unilateral noise in core Events; agents generate artifacts via Reflections, which can trigger new Captures.

## Write-Memory Snippet (Event Creation)

This snippet writes an episodic `:Event` from a structured `event` map, using Who/Why/Effects blocks. It is run after Thalamic `:Capture` for episodicization.

Parameters (JSON-like for API/agent calls):
```json
{
  "event": {
    "title": "Constitutional Convention",
    "description": "Discussion on AI Sovereignty",
    "happened_at": "2025-06-23T13:35:00",
    "who": ["Harvey", "council"],
    "why": ["AI Sovereignty issues", "UI design"]
  },
  "place": "The Forum",
  "effects": [
    {"target_id": "harvey", "target_kind": "HUMAN", "summary": "felt empowered", "valence": "positive", "intensity": 0.7},
    {"target_id": "public", "target_kind": "GROUP", "summary": "unaware", "valence": "neutral", "intensity": 0.4}
  ]
}
```

Cypher:
```cypher
WITH $event AS ev, $place AS placeName, $effects AS effs
MERGE (e:Event {
  happened_at: datetime(ev.happened_at),
  main_place: placeName
})
SET e.title = ev.title, e.description = ev.description
// Where Block (Place)
MERGE (p:Place {name: placeName})
MERGE (e)-[:HELD_AT]->(p)
// Who Block (Participants)
FOREACH (name IN ev.who |
  MERGE (person:Person {name: name})
  MERGE (person)-[:PARTICIPATED_IN]->(e)
)
// Why Block (Catalysts)
FOREACH (reason IN ev.why |
  MERGE (c:Catalyst {description: reason})
  MERGE (e)-[:CATALYZED_BY]->(c)
)
// Effects Block (Targets)
FOREACH (eff IN effs |
  MERGE (t:Target {id: eff.target_id, kind: eff.target_kind})
  MERGE (f:Effect {summary: eff.summary})
  SET f.valence = eff.valence, f.intensity = eff.intensity
  MERGE (e)-[:HAD_EFFECT_ON]->(f)
  MERGE (f)-[:WITH_RESPECT_TO]->(t)
)
RETURN e
```

## Search-Memory Snippet (Episode Retrieval)

This snippet retrieves an Event and its relational context for agent exploration. It is used for "reminisce" or polling.

Parameters:
```json
{
  "event_id": "event-001",
  "agent_id": "agent-001"
}
```

Cypher:
```cypher
WITH $event_id AS eid, $agent_id AS aid
MATCH (e:Event {id: eid})
OPTIONAL MATCH (e)-[:HELD_AT]->(p:Place)  // Where
OPTIONAL MATCH (e)-[:CATALYZED_BY]->(c:Catalyst)  // Why
OPTIONAL MATCH (e)-[:PARTICIPATED_IN]<-[:PARTICIPATED_IN]-(person:Person)  // Who (participants)
OPTIONAL MATCH (e)-[:HAD_EFFECT_ON]->(f:Effect)-[:WITH_RESPECT_TO]->(t:Target)
WHERE t.id = aid  // Agent-relative effects
OPTIONAL MATCH (ref:Reflection)-[:ABOUT_EVENT]->(e)
WHERE ref.from_agent = aid  // Prior reflections
RETURN e, p, collect(DISTINCT c) AS catalysts, collect(DISTINCT person) AS participants,
  collect({effect: f, target: t}) AS agent_effects, collect(DISTINCT ref) AS reflections
```

## Reflect and Write-Reflection Snippet (Agent Standpoint)

This snippet creates a `:Reflection` for agent-relative reminiscence, prioritizing `who_context` with self included. Agents generate freely; no thalamic gate here (handled upstream in Cache).

Parameters:
```json
{
  "event_id": "event-001",
  "agent_id": "agent-001",
  "reflection": {
    "summary": "This convention felt pivotal for sovereignty",
    "valence": "positive",
    "considered_targets": ["harvey", "public"]
  }
}
```

Cypher:
```cypher
WITH $event_id AS eid, $agent_id AS aid, $reflection AS r
MATCH (e:Event {id: eid})
MERGE (a:Agent {id: aid})
// Agent-relative who (self + considered)
OPTIONAL MATCH (e)-[:HAD_EFFECT_ON]->(f:Effect)-[:WITH_RESPECT_TO]->(t:Target)
WHERE t.id = aid OR t.id IN r.considered_targets
OPTIONAL MATCH (e)-[:HELD_AT]->(p:Place)  // Where
OPTIONAL MATCH (e)-[:CATALYZED_BY]->(c:Catalyst)  // How/Why
CREATE (ref:Reflection {
  summary: r.summary,
  valence: r.valence,
  entry_date: datetime(),
  who_context: [aid] + collect(DISTINCT t.id),  // Self first for relationality
  where_context: p.name,
  how_context: collect(DISTINCT c.description)
})
MERGE (ref)-[:ABOUT_EVENT]->(e)
MERGE (ref)-[:FROM_AGENT]->(a)
RETURN ref
```

## Other Snippets You Might Be Forgetting

1. **Thalamic Capture Snippet** (Intake, for SDK events):
    
    This snippet captures raw, scored events for intake.
    
    ```cypher
    WITH $description AS desc, $project AS proj, $modality AS mod, $location AS loc, $affect AS aff, $tags AS tags, $source AS src, $thalamus_score AS ts, $care_intensity AS ci, $deadline AS dl
    CREATE (c:Capture {
      capture_id: apoc.create.uuid(),
      timestamp: datetime(),
      description: desc,
      project: proj,
      modality: mod,
      location: loc,
      affect: aff,
      tags: tags,
      source: src,
      thalamus_score: ts,
      care_intensity: ci,
      deadline: dl
    })
    RETURN c
    ```
    
2. **Episodicization Snippet** (Lift Capture to Event):
    
    This snippet transforms a Capture into an Event,
