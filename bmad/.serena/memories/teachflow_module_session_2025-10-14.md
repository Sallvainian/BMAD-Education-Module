# TeachFlow Module Creation Session

**Date**: 2025-10-14
**User**: Frank
**Session Type**: Module scaffolding and planning

## Session Summary

Successfully created the complete foundational structure for the TeachFlow teaching workflow module through interactive voice-based brainstorming and systematic module generation.

## Module Overview

**Module Name**: TeachFlow
**Module Code**: `teachflow`
**Purpose**: Comprehensive teaching workflow system for managing classroom instruction, behavior management, professional responsibilities, and data analysis
**Location**: `/Users/sallvain/Projects/Sandbox/bmad/teachflow/`

## Components Designed

### Core Agents (4)
1. **Instructional Designer** - Lesson planning, assessments, unit planning, differentiation, goal setting
   - Delegates to: Resource Curator, Accommodation Specialist, Report Generator, Goal Tracker
2. **Behavior Specialist** - Behavior documentation, parent communication, classroom management
   - Delegates to: Report Generator
3. **Professional Writer** - Administrative paperwork and professional documentation
4. **Data Analyst** - Progress tracking, grade analysis, data visualization
   - Delegates to: Report Generator, Goal Tracker

### Supporting Agents (4)
5. **Resource Curator** - Find teaching materials (supports Instructional Designer)
6. **Accommodation Specialist** - Special needs support (supports Instructional Designer)
7. **Report Generator** - Visual reports and dashboards (supports all core agents)
8. **Goal Tracker** - Monitor objectives and progress (supports Instructional Designer, Data Analyst)

### Workflows (9)

**Instructional Designer Workflows**:
- lesson-plan-builder
- unit-planning
- assessment-creation
- differentiation-strategies
- student-goal-setting

**Behavior Specialist Workflows**:
- behavior-incident-report (interview-based with email/note generation)
- classroom-management-plans
- parent-communication-templates

**Data Analyst Workflows**:
- progress-report-generator

## Design Decisions

1. **Delegation Model**: Hierarchical agent system where core agents delegate to specialized supporting agents
2. **Modular Structure**: Each agent and workflow is independent for incremental development
3. **Interview Pattern**: Complex workflows use interview-style data collection
4. **Voice-First Design**: Module planning conducted entirely through voice conversation

## Files Created

```
teachflow/
├── config.yaml                          # Module configuration with delegation rules
├── README.md                            # Complete module documentation
├── TODO.md                              # Detailed development roadmap
├── agents/README.md                     # All 8 agents documented
├── workflows/README.md                  # All 9 workflows documented
├── workflows/[9 directories]            # Workflow structure created
└── _module-installer/
    └── install-module-config.yaml       # Installation configuration
```

## Next Steps

1. **Create first agent**: Run `/bmad:bmb:workflows:create-agent` for Instructional Designer or Behavior Specialist
2. **Reference documentation**: Use `bmad/teachflow/agents/README.md` and `bmad/teachflow/config.yaml`
3. **Build priority workflows**: Focus on lesson-plan-builder, behavior-incident-report, progress-report-generator
4. **Follow roadmap**: Complete development in phases per TODO.md

## Command for Next Session

```bash
/bmad:bmb:workflows:create-agent Create the Instructional Designer agent for the TeachFlow module. Reference bmad/teachflow/agents/README.md and bmad/teachflow/config.yaml for specifications. This agent handles lesson planning, assessment creation, unit planning, differentiation strategies, and student goal setting. It can delegate to Resource Curator, Accommodation Specialist, Report Generator, and Goal Tracker agents.
```

## Success Metrics

- ✅ Complete module structure created
- ✅ All 8 agents documented
- ✅ All 9 workflows planned
- ✅ Delegation patterns defined
- ✅ Development roadmap with phased approach
- ⏳ Agent implementations (0/8 created)
- ⏳ Workflow implementations (0/9 created)
