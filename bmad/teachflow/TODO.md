# TeachFlow Development Roadmap

Generated: 2025-10-14
Status: Module scaffolding complete, components pending creation

---

## Phase 1: Core Agents (High Priority)

Create the four main agents that handle primary teaching responsibilities.

### 1.1 Instructional Designer Agent
**Priority**: 🔴 Critical
**Estimated Time**: 45-60 minutes
**Command**: `/bmad:bmb:workflows:create-agent`

**Scope**:
- Lesson planning and curriculum design
- Assessment creation
- Unit planning
- Differentiation strategies
- Student goal setting
- Can delegate to: Resource Curator, Accommodation Specialist, Report Generator, Goal Tracker

**Key Considerations**:
- Define personality: Professional, pedagogically sound, supportive
- Create command structure for common tasks
- Design delegation logic for supporting agents

---

### 1.2 Behavior Specialist Agent
**Priority**: 🔴 Critical
**Estimated Time**: 45-60 minutes
**Command**: `/bmad:bmb:workflows:create-agent`

**Scope**:
- Behavior incident documentation
- Parent communication drafting
- Classroom management planning
- Intervention strategies
- Behavioral analysis
- Can delegate to: Report Generator

**Key Considerations**:
- Tone: Professional yet empathetic
- Focus on factual, objective language
- Templates for various communication scenarios

---

### 1.3 Professional Writer Agent
**Priority**: 🟡 Important
**Estimated Time**: 30-45 minutes
**Command**: `/bmad:bmb:workflows:create-agent`

**Scope**:
- Administrative paperwork
- Professional correspondence
- Meeting documentation
- Policy interpretation
- General writing support
- No delegation (specialized writer)

**Key Considerations**:
- Formal, professional tone
- Versatile across document types
- Clear, concise communication style

---

### 1.4 Data Analyst Agent
**Priority**: 🟡 Important
**Estimated Time**: 45-60 minutes
**Command**: `/bmad:bmb:workflows:create-agent`

**Scope**:
- Grade analysis and trends
- Student performance tracking
- Data visualization guidance
- Progress monitoring
- Outcome analysis
- Can delegate to: Report Generator, Goal Tracker

**Key Considerations**:
- Data-driven, analytical personality
- Visualization recommendations
- Actionable insights focus

---

## Phase 2: Priority Workflows (High Priority)

Build the three most frequently used workflows first.

### 2.1 Lesson Plan Builder Workflow
**Priority**: 🔴 Critical
**Estimated Time**: 60-90 minutes
**Command**: `/bmad:bmb:workflows:create-workflow`
**Owner**: Instructional Designer

**Type**: Document workflow with template

**Scope**:
- Interactive lesson planning
- Standards alignment
- Activity sequencing
- Assessment integration
- Differentiation suggestions

**Output**: Comprehensive lesson plan document

---

### 2.2 Behavior Incident Report Workflow
**Priority**: 🔴 Critical
**Estimated Time**: 60-90 minutes
**Command**: `/bmad:bmb:workflows:create-workflow`
**Owner**: Behavior Specialist

**Type**: Interactive workflow with dual output

**Scope**:
- Interview-based data collection
- Incident details capture
- Generate parent email
- Generate detailed incident notes
- Suggest follow-up actions

**Output**: Email draft + detailed incident report

---

### 2.3 Progress Report Generator Workflow
**Priority**: 🟡 Important
**Estimated Time**: 60-90 minutes
**Command**: `/bmad:bmb:workflows:create-workflow`
**Owner**: Data Analyst

**Type**: Document workflow with data analysis

**Scope**:
- Data aggregation
- Trend analysis
- Visualization recommendations
- Standards-based reporting
- Growth tracking

**Output**: Student progress report with charts

---

## Phase 3: Supporting Agents (Medium Priority)

Create specialized agents that support core agents.

### 3.1 Resource Curator Agent
**Priority**: 🟢 Enhancement
**Estimated Time**: 30-45 minutes
**Supports**: Instructional Designer

**Scope**:
- Find teaching resources
- Curate lesson materials
- Locate multimedia content
- Organize resource libraries

---

### 3.2 Accommodation Specialist Agent
**Priority**: 🟢 Enhancement
**Estimated Time**: 45-60 minutes
**Supports**: Instructional Designer

**Scope**:
- Accommodation recommendations
- Differentiation strategies
- IEP support
- Inclusive practices
- Accessibility guidance

---

### 3.3 Report Generator Agent
**Priority**: 🟡 Important
**Estimated Time**: 45-60 minutes
**Supports**: All core agents

**Scope**:
- Data visualization
- Report formatting
- Dashboard creation
- Presentation materials
- Summary generation

---

### 3.4 Goal Tracker Agent
**Priority**: 🟢 Enhancement
**Estimated Time**: 30-45 minutes
**Supports**: Instructional Designer, Data Analyst

**Scope**:
- Track learning objectives
- Monitor IEP goals
- Progress check-ins
- Milestone tracking
- Achievement documentation

---

## Phase 4: Additional Workflows (Medium Priority)

Complete the workflow portfolio.

### 4.1 Unit Planning Workflow
**Priority**: 🟡 Important
**Owner**: Instructional Designer
**Type**: Document workflow

**Scope**: Multi-week unit design with aligned objectives

---

### 4.2 Assessment Creation Workflow
**Priority**: 🟡 Important
**Owner**: Instructional Designer
**Type**: Document workflow

**Scope**: Tests, quizzes, rubrics, standards alignment

---

### 4.3 Differentiation Strategies Workflow
**Priority**: 🟢 Enhancement
**Owner**: Instructional Designer
**Type**: Interactive workflow

**Scope**: Generate differentiation plans for diverse learners

---

### 4.4 Student Goal Setting Workflow
**Priority**: 🟢 Enhancement
**Owner**: Instructional Designer
**Type**: Interactive workflow

**Scope**: Facilitate student goal-setting sessions

---

### 4.5 Classroom Management Plans Workflow
**Priority**: 🟢 Enhancement
**Owner**: Behavior Specialist
**Type**: Document workflow

**Scope**: Develop classroom management strategies

---

### 4.6 Parent Communication Templates Workflow
**Priority**: 🟡 Important
**Owner**: Behavior Specialist
**Type**: Action workflow

**Scope**: Generate parent communications for various scenarios

---

## Phase 5: Polish and Integration (Low Priority)

### 5.1 Template Library
- Create shared templates for common documents
- Build template inheritance structure
- Standardize formatting

### 5.2 Delegation Testing
- Test agent delegation patterns
- Verify cross-agent communication
- Optimize workflow handoffs

### 5.3 Documentation Refinement
- Complete agent documentation
- Add workflow examples
- Create usage guides
- Record demo videos (optional)

### 5.4 Data Integration
- Set up data storage patterns
- Create data import/export utilities
- Build analytics dashboard (future)

---

## Quick Commands Reference

### Create New Agent
```bash
/bmad:bmb:workflows:create-agent
```

### Create New Workflow
```bash
/bmad:bmb:workflows:create-workflow
```

### Run Workflow
```bash
/teachflow:workflow-name
```

---

## Recommended Creation Order

**Week 1: Core Foundation**
1. Instructional Designer agent (Day 1-2)
2. Lesson Plan Builder workflow (Day 2-3)
3. Behavior Specialist agent (Day 4)
4. Behavior Incident Report workflow (Day 5)

**Week 2: Expand Core**
5. Professional Writer agent (Day 1)
6. Data Analyst agent (Day 2)
7. Progress Report Generator workflow (Day 3)
8. Unit Planning workflow (Day 4-5)

**Week 3: Supporting Cast**
9. Report Generator agent (Day 1)
10. Resource Curator agent (Day 2)
11. Accommodation Specialist agent (Day 3)
12. Goal Tracker agent (Day 4)

**Week 4: Complete Workflows**
13. Assessment Creation workflow
14. Parent Communication Templates workflow
15. Remaining workflows
16. Testing and refinement

---

## Testing Checklist

After creating each component:

- [ ] Agent loads without errors
- [ ] Agent commands work as expected
- [ ] Workflow executes successfully
- [ ] Output matches expectations
- [ ] Delegation works correctly (if applicable)
- [ ] Documentation is complete
- [ ] Examples are clear and helpful

---

## Notes

### Design Decisions
- **Delegation Model**: Core agents can delegate to supporting agents, creating efficient workflows
- **Modular Design**: Each agent/workflow is independent, allowing incremental development
- **Template-First**: Workflows use templates for consistent, professional outputs
- **Interview Pattern**: Complex workflows use interview-style data collection for better UX

### Future Enhancements
- Integration with external data sources (grade books, LMS)
- Automated report scheduling
- Data visualization dashboard
- Mobile-friendly interfaces
- Multi-language support
- District policy customization

### Known Limitations
- Agents must be created manually using workflows
- No automated testing framework yet
- Templates need manual updates
- Limited data persistence between sessions

---

## Getting Help

**Stuck on agent creation?**
- Review existing agents in `bmad/bmm/agents/` or `bmad/bmb/agents/`
- Check agent creation workflow documentation
- Start simple, add complexity later

**Workflow not working?**
- Verify workflow.yaml configuration
- Check instructions.md for errors
- Test with minimal inputs first
- Review workflow execution logs

**Need inspiration?**
- Study BMM module structure
- Review CIS module patterns
- Look at existing BMAD workflows

---

## Progress Tracking

**Phase 1**: ⏳ 0/4 agents created
**Phase 2**: ⏳ 0/3 workflows created
**Phase 3**: ⏳ 0/4 agents created
**Phase 4**: ⏳ 0/6 workflows created
**Phase 5**: ⏳ Not started

**Overall Completion**: 0% (0/17 core components)

---

Last Updated: 2025-10-14
