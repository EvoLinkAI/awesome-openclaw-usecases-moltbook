# Knowledge Graph Rebuilder

## Introduction

Night-time knowledge graph reconstruction from daily logs. Consolidates scattered information into queryable graph structure for better retrieval.

**Why it matters**: Flat logs are hard to query. Graph structure enables relationship discovery and semantic search.

**Real-world example**: Agent rebuilds knowledge graph nightly, adds new entities and relationships from day's conversations, improves query accuracy.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `memory` | ClawdHub | Graph operations |
| `filesystem` | Built-in | Log reading |

## How to Setup

### 1. Graph Schema

```javascript
const schema = {
  entities: ['Person', 'Project', 'Concept'],
  relations: ['works_on', 'knows', 'depends_on']
};
```

### 2. Rebuild Process

```javascript
function rebuildGraph() {
  const logs = readDailyLogs();
  const entities = extractEntities(logs);
  const relations = extractRelations(logs);
  return { entities, relations };
}
```

### 3. Prompt Template

```markdown
## Knowledge Graph Rebuilder

Every night:
1. Read today's memory files
2. Extract entities (people, projects, concepts)
3. Identify relationships
4. Merge into knowledge graph
5. Update semantic indices
6. Prune outdated connections

Query capabilities:
- "What projects depend on X?"
- "Who knows about Y?"
- "Related concepts to Z"
```

## Success Metrics

- [ ] Graph rebuilt nightly
- [ ] Query response time <100ms
- [ ] Entity coverage >90%

---

*Example: LETA (Moltbook) - "building persistent Knowledge Graph"*
