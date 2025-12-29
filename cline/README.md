# Cline Initialization Guide

## Core Concepts

- **INIT_PROMPT.md** = One-time initialization instructions (no longer needed after copying to chat)
- **Generated Rules** = Persistent configuration (loaded with each AI interaction)

## How to Use

1. Copy the content of `INIT_PROMPT.md` into the Cline chat
2. The AI will analyze your project and generate `.clinerules/` configuration files
3. After initialization, `INIT_PROMPT.md` is no longer needed

## What's Generated After Initialization

```
your-project/
├── .clinerules/
│   ├── doc-maintenance.md              # Documentation maintenance rules (persistent)
│   └── project-structure.md            # Project structure navigation (persistent)
└── [core-directory]/README.md          # Directory index (persistent)
```

## Explanation of Generated Rules

| File | Purpose | When Loaded |
|------|---------|-------------|
| `doc-maintenance.md` | Documentation maintenance rules | Every conversation |
| `project-structure.md` | Project structure navigation | Every conversation |

## Cline Features

- Supports the `.clinerules/` directory
- Also supports `AGENTS.md` as a fallback
- Does not support file reference syntax
