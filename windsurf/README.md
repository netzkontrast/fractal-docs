# Windsurf Initialization Guide

## Core Concepts

- **INIT_PROMPT.md** = One-time initialization instructions (no longer needed after copying to chat)
- **Generated Rules** = Persistent configuration (loaded with each AI interaction)

## How to Use

1. Copy the content of `INIT_PROMPT.md` into the Windsurf chat
2. The AI will analyze your project and generate `.windsurf/rules/` configuration files
3. After initialization, `INIT_PROMPT.md` is no longer needed

## What's Generated After Initialization

```
your-project/
├── .windsurf/
│   └── rules/
│       ├── doc-maintenance.md          # Documentation maintenance rules (persistent)
│       └── project-structure.md        # Project structure navigation (persistent)
└── [core-directory]/README.md          # Directory index (persistent)
```

## Explanation of Generated Rules

| File | Purpose | When Loaded |
|------|---------|-------------|
| `doc-maintenance.md` | Documentation maintenance rules | Always loaded (trigger: always_on) |
| `project-structure.md` | Project structure navigation | Always loaded (trigger: always_on) |

## Windsurf Rules Features

- Supports 4 trigger modes: always_on, manual, model_decision, glob
- Does not support file reference syntax
