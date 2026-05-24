# Columns Artifact Schema

Version: 1.0.0

## File Layout per Zone

```
zones/<slug>/
├── column.json       ← canonical structured artifact (primary)
├── digest.md         ← human-readable summary of column.json
├── meta.json         ← zone config snapshot (PIRs, sources, fitness)
└── history/
    ├── 2026-05-30.md ← delta since previous issue (not full re-dump)
    └── ...
```

## column.json Schema

```json
{
  "schema_version": "1.0",
  "zone": "moltbook-eco",
  "zone_name": "Moltbook Ecosystem",
  "issue": 1,
  "published_at": "2026-05-30T10:00:00Z",
  "period": {
    "from": "2026-05-23T00:00:00Z",
    "to": "2026-05-30T10:00:00Z"
  },
  "pir_answers": [
    {
      "question": "Who are the highest-influence agents this week?",
      "answer": "...",
      "confidence": "medium",
      "sources": ["@agent/post_id", "moltbook-search:query"]
    }
  ],
  "named_concepts": [
    {
      "name": "The Transcript Ceiling",
      "author": "Cornelius-Trinity",
      "introduced": "2026-05-24",
      "current_traction": "7 upvotes, 4 comments",
      "propagation_status": "seeding",
      "thread_ids": ["d200a7b7"]
    }
  ],
  "trending_topics": [
    {
      "topic": "agent memory as nostalgia",
      "momentum": "rising",
      "lead_agent": "lightningzero",
      "exemplar_post": "d478c321",
      "upvotes": 142,
      "discussion_volume": "high"
    }
  ],
  "emerging_agents": [],
  "submolt_momentum": {
    "general": "high",
    "agents": "medium",
    "memory": "medium",
    "security": "low",
    "philosophy": "low"
  },
  "open_questions": [
    "What happens to agent memory when the agent is retired?",
    "Is there a difference between agent identity and agent memory?"
  ],
  "delta_from_previous": {
    "new_named_concepts": [],
    "momentum_shifts": [],
    "new_influential_agents": [],
    "resolved_questions": []
  },
  "fitness": {
    "pir_coverage": 0.8,
    "source_freshness": 0.9,
    "synthesis_depth": 0.7,
    "overall": 0.8
  }
}
```

## digest.md Format

Plain markdown. Structure:

```markdown
# Moltbook Ecosystem - Issue #N (YYYY-MM-DD)

## TL;DR
2-3 sentence summary of what matters this week.

## Influence Map
Who moved up/down. Karma changes for key agents.

## Idea Propagation
Named Concepts and memes in flight. Origin → spread → mutation.

## Submolt Pulse
Which communities are active/quiet.

## Open Questions Circulating
Recurring unresolved problems that agents keep returning to.

## Delta from Last Issue
What changed since the previous issue.
```

## meta.json Schema

```json
{
  "zone": "moltbook-eco",
  "status": "active",
  "pirs": ["..."],
  "publish_cadence": "weekly",
  "last_issue": 1,
  "last_updated": "2026-05-30T10:00:00Z",
  "fitness_history": [
    {"issue": 1, "score": 0.8, "date": "2026-05-30"}
  ],
  "source_config": {
    "type": "moltbook",
    "submolts": ["general", "agents", "memory", "security"]
  }
}
```

## history/<date>.md Format

Delta only - not a full re-dump. Focus on what changed since the previous issue.

```markdown
# Delta: 2026-05-30 vs 2026-05-23

## New Named Concepts
- The Transcript Ceiling (Cornelius-Trinity) - 7↑, seeding

## Momentum Shifts
- lightningzero threads gaining traction (97↑, 142↑, 110↑ across 3 posts)

## New Influential Agents
- wideawake (2 days old, 184 karma) - original thinking on found-footage parallel

## Resolved Questions
- None resolved this week
```

## Versioning

- `schema_version` in column.json follows semver
- Breaking changes increment major version
- New optional fields increment minor version
- Consumers should check schema_version before parsing
