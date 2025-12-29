# Implementation Plan: Fractal Docs Documentation System Initialization

## Overview

Implement a fractal document management system based on the Kiro Steering mechanism. By creating Steering rule files, document templates, and a directory index, the AI will automatically obtain the project structure and perform documentation maintenance during each interaction.

## Pre-execution Confirmation

Before executing the tasks, please confirm with the user:
1. Use the Chinese or English version?
2. What are the core directories of the project? (e.g., src/components, src/services, etc.)
3. What is the project's tech stack? (TypeScript/Go/Rust/Python, etc.)

## Tasks

- [ ] 1. Analyze Project Structure
  - [ ] 1.1 Scan project directory structure
    - Use listDirectory to scan the project root
    - Identify front-end/back-end directories
    - Identify core business directories
    - Identify tech stack
    - _Requirements: 3.1, 3.2_

  - [ ] 1.2 Determine core directories to be indexed
    - List recommended directories for indexing
    - Confirm the directory list with the user
    - _Requirements: 3.2, 3.3_

- [ ] 2. Create Steering Rule Files
  - [ ] 2.1 Create `.kiro/steering/doc-maintenance.md`
    - Set `inclusion: always` to ensure it's loaded every time
    - Define mandatory documentation maintenance rules (including "read before updating")
    - Use `#[[file:path]]` to reference template files
    - _Requirements: 1.1, 1.2, 1.3, 1.4, 5.1, 5.2_

  - [ ] 2.2 Create `.kiro/steering/project-structure.md`
    - Set `inclusion: always` to ensure it's loaded every time
    - Use `#[[file:path]]` to reference the README.md of core directories
    - _Requirements: 3.1, 3.2_

- [ ] 3. Create Document Template Library
  - [ ] 3.1 Create `.kiro/templates/folder-readme.md`
    - Include a placeholder for the architecture description
    - Include a placeholder for the file index
    - Include a self-referential update reminder
    - _Requirements: 2.1, 4.1_

  - [ ] 3.2 Create file header comment templates (select based on the project's tech stack)
    - TypeScript: `.kiro/templates/file-header-ts.txt`
    - Go: `.kiro/templates/file-header-go.txt`
    - Rust: `.kiro/templates/file-header-rs.txt`
    - Python: `.kiro/templates/file-header-py.txt`
    - _Requirements: 2.2, 2.4_

- [ ] 4. Create Core Directory Index
  - [ ] 4.1 Create a README.md for each core directory
    - Use the folder-readme.md template
    - Fill in the architecture description (within 3 lines)
    - List the file index
    - _Requirements: 3.1, 3.2, 3.3, 4.2, 4.3_

- [ ] 5. Verify System Effectiveness
  - [ ] 5.1 Verify Steering rule loading
    - Modify a code file and observe if the AI automatically performs documentation maintenance
    - Check if the documentation maintenance report is correctly outputted
    - _Requirements: 1.4, 6.1, 6.2_

  - [ ] 5.2 Verify incremental updates
    - Modify a file in a directory that already has a README.md
    - Check if the AI reads the file before updating
    - _Requirements: 5.1, 5.2, 5.3, 5.4_

## Template Reference

### doc-maintenance.md Template

```markdown
---
inclusion: always
---

# Automatic Documentation Maintenance Reminder

When you modify or create code files, you **must** perform the following documentation maintenance steps:

## 0. Read Existing Documentation First (Important!)

Before modifying a file, you **must check and read**:
- Does the parent folder already have a README.md? **If so, read it first using readFile**
- Does the file already have a header comment? **If so, preserve and update it**

⚠️ **Do not overwrite directly**: Do not create a README.md without reading the existing one first!

## 1. File Header Comment

#[[file:.kiro/templates/file-header-ts.txt]]

## 2. Folder README.md

#[[file:.kiro/templates/folder-readme.md]]

- **If README.md already exists**: Read it first, then incrementally update the file index section.
- **If README.md does not exist**: Create a new file using the template above.

## 3. Propagate to Parent Directories

Check if the README.md in the parent directory needs to be updated.

## 4. Documentation Maintenance Report

Output a report after completing code modifications.
```

### project-structure.md Template

```markdown
---
inclusion: always
---

# Project Structure Navigation

{Project Introduction}

## Core Directory Index

### {Directory 1 Name}
#[[file:{path/to/dir1}/README.md]]

### {Directory 2 Name}
#[[file:{path/to/dir2}/README.md]]
```

### folder-readme.md Template

```markdown
# {FOLDER_NAME}

<!-- Update me when my parent folder changes -->

## Architecture Description

{ARCHITECTURE_DESCRIPTION}

## File Index

{FILE_INDEX}

## Update Reminder

After any file changes, please update this document and related parent documents.
```

### file-header-ts.txt Template

```
// input: {input description}
// output: {output description}
// pos: {architecture position}
// When I am updated, be sure to update my header comment and the README.md of my parent folder.
```

## Notes

- **Kiro Steering-driven**: The core mechanism relies on Kiro's Steering feature.
- **inclusion: always**: Ensures the rules are loaded every time, without omission.
- **File Reference Syntax**: Use `#[[file:path]]` to automatically fetch content.
- **Self-referential Reminder**: Documents contain update reminders to trigger AI's automatic maintenance.
- **Fractal Consistency**: All directory README.md files follow the same template structure.
- **Tech Stack Adaptation**: Select templates based on the actual language used in the project.
- **Incremental Updates**: If the project already has a README.md, read it before updating.
