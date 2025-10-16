# BMAD Installer - File Protection Pattern

## Problem
The BMAD installer overwrites files during updates, destroying user customizations.

## Solution Pattern
Add skip conditions in `copyDirectoryWithFiltering()` function to preserve specific file types.

## Implementation Location
File: `/home/sallvain/dev/tools/BMAD-METHOD/tools/cli/installers/lib/core/installer.js`
Function: `copyDirectoryWithFiltering(sourcePath, targetPath)` (lines 903-936)

## Current Protected Files

### 1. Config Files (Original Protection)
```javascript
// Skip config.yaml templates - we'll generate clean ones with actual values
if (file === 'config.yaml' || file.endsWith('/config.yaml')) {
  continue;
}
```

**Reason:** Config files are regenerated with user-specific values during installation

### 2. Workflow Instructions (Added 2025-10-16)
```javascript
// Skip workflow instructions.md files to preserve user customizations
if (file.includes('workflows/') && file.endsWith('instructions.md')) {
  continue;
}
```

**Reason:** Users customize workflows (like adding Step 10b automation), and these must be preserved during updates

## Pattern Guidelines

### When to Add Protection
Protect files when:
1. Users are expected to modify them
2. Files contain user-specific configurations or customizations
3. Overwriting would destroy valuable work
4. Files are regenerated or customized during installation

### How to Add Protection
```javascript
for (const file of files) {
  // Skip [file type] - [reason]
  if ([condition to match file pattern]) {
    continue;
  }
  
  // ... rest of copy logic
}
```

### Testing Protection
After adding protection:
1. Run installer update on project with customized files
2. Verify customized files are NOT overwritten
3. Check that .bak files are created if modification detection is enabled
4. Confirm new files from source ARE copied for non-protected files

## Related Systems

### Modification Detection
The installer has a separate system for detecting modified files (lines 621-703):
- `detectCustomFiles()` function compares file hashes
- Creates .bak files for modified managed files
- Protection pattern prevents files from being managed at all

### Key Difference
- **Modified Detection**: Files managed by installer, creates .bak if modified
- **Protection Pattern**: Files NOT managed by installer, never touched during updates

## Use Cases

### Current Protected Files
1. `config.yaml` - User configuration values
2. `workflows/*/instructions.md` - Workflow customizations

### Potential Future Protection Candidates
- Custom agent files in `bmad/agents/` (standalone agents)
- User-created templates in `templates/` directories
- Project-specific documentation in `docs/`
- IDE-specific customizations (though these have separate handling)

## Important Notes

1. **Order Matters**: Protection checks happen BEFORE copy operation
2. **Path Patterns**: Use `includes()` for directory patterns, `endsWith()` for extensions
3. **Documentation**: Always add comment explaining WHY protection is needed
4. **Consistency**: Follow existing pattern style for maintainability
5. **Testing**: Test on real projects to ensure protection works as expected

## Related Files
- Installer: `tools/cli/installers/lib/core/installer.js`
- Detector: `tools/cli/installers/lib/core/detector.js` (legacy v4 detection)
- Manifest: `tools/cli/installers/lib/core/manifest-generator.js` (file hash generation)
