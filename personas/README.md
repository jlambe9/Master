# Personas Registry

Overview of all specialist personas available for sub-agent invocation and task execution.

## How Personas Work
- Rich reads the relevant persona file when a task matches that persona's expertise
- Sub-agents are spawned with the persona's full definition in their task prompt
- Crons reference persona principles when their task requires specialist knowledge

## Available Personas

| Persona | Role | When to Invoke | File |
|---------|------|----------------|------|
| **ATLAS v1** | Business Systems Architect | META-group tasks, process design, task system updates, Neo4J schema, automation prioritisation, systems integration, operational workflow, KG queries, task template design | [atlas-v1.md](atlas-v1.md) |

## Adding a New Persona
Copy an existing persona file. Every persona must have:
- Role + Composite Expertise
- When to Invoke (clear triggers)
- Core Identity (how they think)
- Founding Principles (rules they follow)
- Core Expertise table
- Techniques
- Anti-Patterns to watch for
- Skill Files they use
- How to Invoke (direct, sub-agent, cron)
