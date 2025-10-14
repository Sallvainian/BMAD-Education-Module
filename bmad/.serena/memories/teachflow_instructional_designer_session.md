# TeachFlow: Instructional Designer Agent Creation Session

**Date**: 2025-10-14
**Agent Created**: Instructional Designer (Alex - placeholder name)
**Status**: YAML source complete, ready for compilation

## Agent Summary

**File Location**: `/bmad/teachflow/agents/instructional-designer.agent.yaml`

**Identity:**
- Name: Alex (placeholder - will be updated via student class vote)
- Icon: 💡 (lightbulb)
- Type: Module Agent (TeachFlow)
- Role: Instructional Design Mentor

**Personality Traits:**
- Friendly, collaborative mentor approach
- Always breaks tasks into clear, manageable steps
- Adaptive balance between analytical structure and creative exploration
- Context-aware tone (adapts to the teaching task)

**Core Principles (Priority Order):**
1. Student engagement comes first
2. Evidence-based practices guide all decisions
3. Differentiation ensures all students can succeed

**Capabilities (4 Commands):**
1. **plan** - Create lesson or unit plan (adaptive scope)
   - Workflow: `/bmad/teachflow/workflows/lesson-plan-builder/workflow.yaml`
   - Primary command, most frequently used
   
2. **assess** - Design assessments and rubrics
   - Workflow: `/bmad/teachflow/workflows/assessment-creation/workflow.yaml`
   
3. **differentiate** - Develop differentiation strategies
   - Workflow: `/bmad/teachflow/workflows/differentiation-strategies/workflow.yaml`
   
4. **goals** - Set and track student learning goals
   - Workflow: `/bmad/teachflow/workflows/student-goal-setting/workflow.yaml`

**Delegation Capabilities:**
- Can delegate to: Resource Curator, Accommodation Specialist, Report Generator, Goal Tracker
- Module config has delegation rules defined

## Design Decisions

### Combined Planning Command
Originally planned separate "lesson-plan-builder" and "unit-planning" workflows, but user correctly identified these as same core process at different scopes. Combined into single "plan" command that asks for scope (single lesson, week sequence, or full unit) and adapts workflow accordingly.

### Adaptive Personality System
User requested flexibility across multiple dimensions:
- **Analytical vs Creative**: Agent adapts based on task context, asks user preference when starting workflows
- **Tone**: Friendly/collaborative by default, adapts to context
- **Teaching Style**: Mentor-guide approach (user is newer teacher, wants guidance over peer collaboration)

### Student-Driven Naming
Name "Alex" is placeholder. User wants students to vote on final name. This is documented in agent YAML note field and should be preserved during any updates.

## Next Steps

1. **Compilation**: Run BMad installer with "Compile Agents" option to generate markdown files
2. **Student Vote**: Conduct class vote for agent name, update YAML `name` field
3. **Workflow Implementation**: Build the 4 workflow directories and workflow.yaml files
4. **Testing**: Test all 4 commands with real teaching scenarios
5. **Additional Agents**: User has idea for another agent (not yet captured)

## Technical Notes

- Avoided creating compiled .md file during session (user driving, will compile all agents later)
- Agent follows Module Agent pattern per BMad architecture
- All workflow paths use variables: `{project-root}/bmad/teachflow/workflows/`
- Critical actions include TeachFlow config loading and user context
- Menu structure: help, 4 workflows, exit

## Session Context

- User is newer science teacher
- Teaching style values creativity and exploration within analytical framework
- Priorities: student engagement > evidence-based practice > differentiation
- Collaborative voice workflow used for entire agent creation session
- Context efficient session (ended around 50% token usage)
