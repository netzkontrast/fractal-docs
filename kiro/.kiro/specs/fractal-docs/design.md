# Design Document

## Overview

Fractal Docs is implemented based on Kiro's Steering mechanism. Through auto-loading rule files and file reference syntax, it allows the AI to obtain project structure context and automatically perform documentation maintenance tasks during each interaction.

## Architecture

### Kiro Steering-driven Design

```
Fractal Docs System
├── Steering Rules (.kiro/steering/)
│   ├── doc-maintenance.md      # Documentation maintenance rules (always)
│   └── project-structure.md    # Project structure navigation (always)
├── Document Template Library (.kiro/templates/)
│   ├── folder-readme.md        # Folder README template
│   └── file-header-*.txt       # File header comment template
└── Directory Index (README.md in each directory)
    └── Referenced in Steering via #[[file:path]]
```

### Steering Mechanism Workflow

```
┌─────────────────┐
│   Kiro Startup  │
└────────┬────────┘
         │
         ▼
┌─────────────────────────────────┐
│ Load .kiro/steering/*.md       │
│ (files with inclusion: always)  │
└────────┬────────────────────────┘
         │
         ▼
┌─────────────────────────────────┐
│ Parse #[[file:path]] references │
│ Fetch README.md content into context│
└────────┬────────────────────────┘
         │
         ▼
┌─────────────────────────────────┐
│ AI gets complete project structure + maintenance rules │
└────────┬────────────────────────┘
         │
         ▼
┌─────────────────────────────────┐
│ Automatically perform doc maintenance when code changes │
│ Output documentation maintenance report                │
└─────────────────────────────────┘
```

## Components and Interfaces

### 1. Steering Rule Files

#### doc-maintenance.md
Enforces documentation maintenance rules, loaded with every interaction. Includes:
- Step 0: Read existing documentation first (to prevent overwriting)
- Step 1: File header comment
- Step 2: Folder README.md
- Step 3: Propagate to parent directories
- Step 4: Documentation maintenance report

#### project-structure.md
Project structure navigation, referencing core directory README.md files via `#[[file:path]]`.

### 2. Document Template Library

#### folder-readme.md
```markdown
# {FOLDER_NAME}

<!-- Update me when my parent folder changes -->

## Architecture Description

{ARCHITECTURE_DESCRIPTION}

## File Index

{FILE_INDEX}
```

#### file-header-*.txt
```
// input: {INPUT_DESCRIPTION}
// output: {OUTPUT_DESCRIPTION}
// pos: {POSITION_DESCRIPTION}
// When I am updated, be sure to update my header comment and the README.md of my parent folder.
```

### 3. Directory Index README.md

Each core directory has a README.md, including:
- Architecture description (within 3 lines)
- File index (file name + feature description)
- Self-referential update reminder

## Known Issues and Solutions

### Issue 1: AI overwrites existing documentation without reading first

**Solution**: Add "Step 0: Read existing documentation first" to doc-maintenance.md to explicitly prohibit direct overwriting.

### Issue 2: The self-referential reminder is a comment, not an executable instruction

**Solution**: Use the self-referential reminder in conjunction with mandatory rules. The key is to ensure that all directories requiring maintenance are referenced in project-structure.md.
