# Fractal Docs Initialization Task

Please help me initialize the Fractal Docs self-maintaining documentation system in this project.

## What you need to do

### 1. Analyze Project Structure

- Scan the project directory structure
- Identify the tech stack (TypeScript/Go/Rust/Python, etc.)
- Determine the core business directories (e.g., src/components, src/services, etc.)
- List the recommended directories for indexing and let me confirm

### 2. Create CLAUDE.md

Create `CLAUDE.md` in the project root directory, including:
- Basic project information
- Tech stack description
- Reference to rule files in `.claude/rules/`

### 3. Create .claude/rules/ Rule Files

#### 3.1 Create `.claude/rules/doc-maintenance.md`

```markdown
---
paths:
  - "**/*.ts"
  - "**/*.tsx"
  - "**/*.js"
  - "**/*.jsx"
  - "**/*.go"
  - "**/*.rs"
  - "**/*.py"
---

# Documentation Maintenance Rules

When you modify or create code files, you **must** perform the following steps:

## 0. Read Existing Documentation First (Important!)

Before modifying a file, you **must check and read**:
- Does the parent folder already have a README.md? **If so, read it first**
- Does the file already have a header comment? **If so, preserve and update it**

⚠️ **Do not overwrite directly**!

## 1. File Header Comment

Each code file must have a standard three-line comment:
// input: {input description}
// output: {output description}
// pos: {architecture position}

## 2. Folder README.md

After modifying a file, update the README.md of its parent folder:
- If it already exists: read it first, then incrementally update the file index
- If it doesn't exist: create a new file

## 3. Propagate to Parent Directories

Check if the README.md in the parent directory needs to be updated.

## 4. Documentation Maintenance Report

Output a report upon completion.
```

#### 3.2 Create `.claude/rules/project-structure.md`

Based on the analysis results, use the `@path/to/README.md` syntax to reference the core directories.

### 4. Create README.md for Core Directories

For each core directory, create a README.md with the following format:

```markdown
# {Directory Name}

<!-- Update me when my parent folder changes -->

## Architecture Description

{A description within 3 lines}

## File Index

- `file1.ts` - Feature description
- `subfolder/` - Subdirectory description
```

### 5. Confirm Completion

Tell me which files were generated upon completion.

## Language Preference

Please use English to generate all documentation and comments.
