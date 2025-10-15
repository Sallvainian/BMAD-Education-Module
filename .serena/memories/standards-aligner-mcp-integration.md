# Standards Aligner MCP Integration - Session Update

**Date:** 2025-10-15
**Session Type:** Standards Aligner v2.0 - MCP Integration Upgrade
**Status:** Configuration Complete, Testing Pending Restart

## Changes Made

### 1. Standards Aligner v2.0 YAML Update
**File:** `/bmad/teachflow/agents/standards-aligner.agent.yaml`

**Major Changes:**
- ✅ Migrated from direct JSON file access to NGSS MCP Server integration
- ✅ Version bumped: 1.0.0 → 2.0.0
- ✅ Added `mcp_integration` section documenting 5 MCP tools
- ✅ Updated all 11 commands to use MCP tool calls instead of file I/O
- ✅ Enhanced persona identity with MCP awareness
- ✅ Updated critical_actions to verify MCP connection on startup
- ✅ Added MCP-specific performance targets (<500ms latency)

**MCP Tools Mapping:**
```yaml
get_standard → *lookup-standard, *get-3d-components
find_by_driving_question → *lookup-question
get_3d_components → *get-3d-components, *get-depth-boundaries
search_by_domain → *list-driving-questions, *search-standards
search_standards → *search-standards, *map-curriculum
```

**Architecture:**
```
User/Agent Command
      ↓
Standards Aligner (Pedagogical Intelligence Layer)
  - Interprets requests
  - Adds educational context
  - Formats for teaching agents
      ↓
NGSS MCP Server (Data Access Layer)
  - Multi-index lookups (O(1) for codes)
  - Fuzzy keyword matching
  - Relevance scoring
      ↓
Standards Database (55 NGSS MS standards)
```

### 2. MCP Configuration Created
**File:** `/home/sallvain/dev/personal/BMAD-Education-Module/.mcp.json`

```json
{
  "mcpServers": {
    "ngss": {
      "command": "node",
      "args": [
        "/home/sallvain/dev/mcp-servers/NGSS-MCP/dist/server/index.js"
      ],
      "disabled": false
    }
  }
}
```

**Server Location:** `/home/sallvain/dev/mcp-servers/NGSS-MCP/dist/server/index.js`
**Server Status:** Compiled and ready (Epic 1 Story 2 complete)

## NGSS MCP Server Capabilities

**Database Coverage:**
- 55 NGSS Middle School Standards
  - Physical Science (MS-PS): 19 standards
  - Life Science (MS-LS): 21 standards
  - Earth & Space Science (MS-ESS): 15 standards
- 100% 3D completeness (SEP + DCI + CCC for all)
- Database size: 80 KB (optimized, clean text)

**Performance Characteristics:**
- Multi-index architecture (4 indexes)
- O(1) lookups for standard codes (Map index)
- O(k) keyword search where k = query words
- Relevance scoring for search results
- <1 second response times

**5 MCP Tools Available:**
1. **get_standard**: Direct lookup by code (MS-LS1-6)
2. **find_by_driving_question**: Fuzzy keyword matching for questions
3. **get_3d_components**: Extract isolated SEP/DCI/CCC framework
4. **search_by_domain**: Filter by Physical/Life/Earth Science
5. **search_standards**: Full-text search with optional domain filter

## Benefits of MCP Integration

**Separation of Concerns:**
- Data Access: NGSS MCP Server (optimized database operations)
- Pedagogical Intelligence: Standards Aligner (educational context, interpretation)

**Performance Improvements:**
- Multi-index lookups vs sequential JSON parsing
- Fuzzy matching built-in (driving questions)
- Relevance scoring for search results
- Optimized for common query patterns

**Maintainability:**
- Database changes don't affect Standards Aligner
- Can upgrade MCP server independently
- Other agents can use NGSS server directly if needed
- Clear API contract via MCP tools

**Architecture Quality:**
- MCP-native approach (vs file I/O hack)
- Follows best practices for tool separation
- Scales better for future expansion

## Testing Status

**Configuration:** ✅ Complete
- `.mcp.json` created with NGSS server entry
- Server compiled and ready at correct path
- All 5 tools documented in Standards Aligner

**Testing:** ⏳ Pending Claude Code Restart
- MCP client needs restart to load new server config
- After restart, can test with:
  ```
  ListMcpResourcesTool(server='ngss')
  # Should show 5 tools available
  ```

**Next Verification Steps:**
1. Restart Claude Code to load NGSS server
2. Verify server connection: `ListMcpResourcesTool(server='ngss')`
3. Test tool call: Call `get_standard` with code='MS-LS1-6'
4. Verify Standards Aligner can delegate to MCP tools
5. Test end-to-end: Instructional Designer → Standards Aligner → NGSS MCP

## Integration Points for Phase 2

**Instructional Designer (Next Agent):**
- Will delegate to Standards Aligner via `*lookup-standard`
- Standards Aligner will call NGSS MCP `get_standard` tool
- Returns complete 3D components for lesson planning
- Expected workflow:
  ```
  Teacher: "Plan photosynthesis lesson"
  Instructional Designer: Identifies standard MS-LS1-6
  → Calls Standards Aligner *lookup-standard MS-LS1-6
  Standards Aligner: Verifies standard exists
  → Calls NGSS MCP get_standard(code='MS-LS1-6')
  NGSS MCP: Returns full standard with 3D components
  Standards Aligner: Adds pedagogical context, formats for ID
  → Returns: SEP, DCI, CCC + depth boundaries
  Instructional Designer: Builds 3D-informed lesson plan
  ```

**Alpha - Student Support Agent (Phase 4):**
- Will delegate to Standards Aligner via `*lookup-question`
- Standards Aligner will call NGSS MCP `find_by_driving_question` tool
- Returns lesson scope for precise student support
- Expected workflow:
  ```
  Student: "How do plants get energy?" (driving question)
  Alpha: Needs 3D scope to teach correctly
  → Calls Standards Aligner *lookup-question "how do plants get energy"
  Standards Aligner: Normalizes question
  → Calls NGSS MCP find_by_driving_question(query='plants energy')
  NGSS MCP: Fuzzy matches → MS-LS1-6 (photosynthesis)
  Standards Aligner: Adds lesson scope + depth boundaries
  → Returns: 3D components + what to teach/not teach
  Alpha: Teaches within precise scope (no over-teaching)
  ```

## Files Modified

1. `/bmad/teachflow/agents/standards-aligner.agent.yaml` (v1.0.0 → v2.0.0)
2. `/home/sallvain/dev/personal/BMAD-Education-Module/.mcp.json` (created)

## Related Documentation

- NGSS MCP Server: `/home/sallvain/dev/mcp-servers/NGSS-MCP/README.md`
- Server Implementation: `/home/sallvain/dev/mcp-servers/NGSS-MCP/SERVER-IMPLEMENTATION.md`
- Extraction Results: `/home/sallvain/dev/mcp-servers/NGSS-MCP/EXTRACTION-RESULTS.md`
- Database: `/home/sallvain/dev/mcp-servers/NGSS-MCP/data/ngss-ms-standards.json` (80 KB, 55 standards)

## Success Metrics

| Metric | Target | Status |
|--------|--------|--------|
| MCP Integration | Complete | ✅ Done |
| Standards Aligner v2.0 | Updated | ✅ Done |
| Configuration Created | .mcp.json | ✅ Done |
| Server Availability | ngss server | ⏳ After restart |
| Tool Count | 5 tools | ⏳ After restart |
| End-to-End Test | Full workflow | ⏳ Phase 2 |

## Next Session Tasks

1. **Restart Claude Code** to load NGSS MCP server
2. **Verify Server Connection:** Use ListMcpResourcesTool to confirm 5 tools available
3. **Test Tool Calls:** Try get_standard, search_standards, find_by_driving_question
4. **Compile Standards Aligner:** Run BMAD installer to generate XML
5. **Phase 2 Start:** Create Instructional Designer agent with Standards Aligner delegation

## Notes

**Why MCP Integration Matters:**
- TeachFlow's quality depends on accurate 3D component provision
- MCP architecture scales better than file I/O
- Clear separation enables independent evolution of data (MCP) and pedagogy (Agent)
- Future agents can use NGSS server directly without going through Standards Aligner

**Critical Success Factor:**
Standards Aligner is single point of failure for both Instructional Designer and Alpha. MCP integration makes it more robust by delegating data access to specialized server with optimized indexes and error handling.
