# Cursor Initialization Guide

## Core Concepts

- **INIT_PROMPT.md** = One-time initialization instructions (no longer needed after copying to chat)
- **Generated Rules** = Persistent configuration (loaded with each AI interaction)

## How to Use

1. Copy the content of `INIT_PROMPT.md` into the Cursor chat
2. The AI will analyze your project and generate `.cursor/rules/` configuration files
3. After initialization, `INIT_PROMPT.md` is no longer needed

## What's Generated After Initialization

```
your-project/
├── .cursor/
│   └── rules/
│       ├── doc-maintenance.mdc         # Documentation maintenance rules (persistent)
│       └── project-structure.mdc       # Project structure navigation (persistent)
└── [core-directory]/README.md          # Directory index (persistent)
```

## Explanation of Generated Rules

| File | Purpose | When Loaded |
|------|---------|-------------|
| `doc-maintenance.mdc` | Documentation maintenance rules | When code files are modified (globs match) |
| `project-structure.mdc` | Project structure navigation | Every conversation (alwaysApply: true) |

## Cursor Rules Features

- Uses the `.mdc` extension
- Supports `globs` for conditional loading
- Supports `@filename` for file references
