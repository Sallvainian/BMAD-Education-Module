# Agent Creation & Installation Flow

## Creating Agents Properly
- Use `/bmad:bmb:workflows:create-agent` workflow (10 interactive steps)
- Creates `.agent.yaml` source file in `bmad/{module}/agents/`
- Workflow handles: persona, commands, naming, validation

## Making Module Available in Installer
- Module must exist in `/home/sallvain/dev/tools/BMAD-METHOD/src/modules/{module-code}/`
- Requires `_module-installer/install-menu-config.yaml` with:
  - `code:` module code
  - `name:` display name for installer menu
  - `description:` what the module does
  - `default_selected: false`

## Installation Process
- Run BMAD installer from BMAD-METHOD
- Module appears in selection menu
- Installer copies module to target project's `bmad/{module-code}/`
- During install, compiles `.agent.yaml` → `.md` files
- Updates manifest at `bmad/_cfg/manifest.yaml`

## Key Discovery
TeachFlow needed to exist in **both places**:
- **Source**: `/dev/tools/BMAD-METHOD/src/modules/teachflow/` (for installer to find it)
- **Target**: `/dev/personal/BMAD-Education-Module/bmad/teachflow/` (installed instance)

## Result
Atlas agent now compiles and installs successfully as part of TeachFlow module.

## Workflow Enhancement - Step 10b Added
Added automated installation step to `/bmad/bmb/workflows/create-agent/instructions.md`:

**Step 10b: "Automated installation to BMAD-METHOD"**
- **Conditional**: Only for module agents (`if="agent_type == 'module'"`)
- **Optional**: User can skip (`optional="true"`)
- **Auto-detects** BMAD-METHOD in common locations:
  - `/home/sallvain/dev/tools/BMAD-METHOD`
  - `{project-root}/../BMAD-METHOD`
  - `~/dev/tools/BMAD-METHOD`

**Automation Steps:**
1. Verifies/creates module structure in BMAD-METHOD source
2. Copies agent YAML to source modules directory
3. Creates/verifies `install-menu-config.yaml` for installer
4. Compiles agent using build CLI: `node tools/cli/bmad-cli.js build {agent} --directory {project}`
5. Updates project manifest to register module
6. Offers immediate testing of installed agent

**Fallback:**
- If BMAD-METHOD not found: Provides clear manual installation instructions
- If compilation fails: Shows error and manual build command

**Pattern Compliance:**
- Follows existing workflow patterns (like step 8b)
- Uses proper XML tags: `<action>`, `<check>`, `<ask>`
- Maintains conversational voice with user-facing messages
- Includes `<template-output>automated_installation</template-output>`
- Proper variable syntax: `{{agent_name}}`, `{project-root}`

**Impact:**
Eliminates manual installation work. Future module agents created through workflow can be automatically:
- Copied to BMAD-METHOD source
- Compiled to executable format
- Registered in installer
- Ready for distribution and use

The workflow now handles complete agent lifecycle: creation → compilation → installation → activation.
