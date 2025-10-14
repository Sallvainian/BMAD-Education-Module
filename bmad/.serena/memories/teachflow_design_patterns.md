# TeachFlow Design Patterns

## Agent Delegation Architecture

Core agents delegate to specialized supporting agents:

- **Instructional Designer** → Resource Curator, Accommodation Specialist, Report Generator, Goal Tracker
- **Behavior Specialist** → Report Generator
- **Data Analyst** → Report Generator, Goal Tracker
- **Professional Writer** → (no delegation)

## Workflow Types

1. **Document Workflows**: Generate polished documents using templates (lesson-plan-builder, unit-planning)
2. **Interactive Workflows**: Interview-based data collection (behavior-incident-report, differentiation-strategies)
3. **Action Workflows**: Quick generation without extensive templates (parent-communication-templates)

## Module Organization

```
teachflow/
├── agents/          # Self-contained agent configurations
├── workflows/       # Grouped by owner agent
├── templates/       # Shared reusable templates
├── data/           # Persistent storage
└── _module-installer/  # Installation infrastructure
```

## Key Principles

- **Agent Independence**: Each agent functions standalone
- **Workflow Ownership**: Clear owner but can be called directly
- **Template Sharing**: Common templates accessible to all
- **Voice-First**: Designed for voice interaction (1.5x speed, brevity)
