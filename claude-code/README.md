# Claude Code Initialization Guide

## Core Concepts

- **INIT_PROMPT.md** = One-time initialization instructions (no longer needed after copying to chat)
- **Generated Rules** = Persistent configuration (loaded with each AI interaction)

## How to Use

1. Copy the content of `INIT_PROMPT.md` into the Claude Code chat
2. The AI will analyze your project and generate configuration files
3. After initialization, `INIT_PROMPT.md` is no longer needed

## What's Generated After Initialization

```
your-project/
├── CLAUDE.md                           # Project configuration (persistent)
├── .claude/
│   └── rules/
│       ├── doc-maintenance.md          # Documentation maintenance rules (persistent)
│       └── project-structure.md        # Project structure navigation (persistent)
└── [core-directory]/README.md          # Directory index (persistent)
```

## Explanation of Generated Rules

| File | Purpose | When Loaded |
|------|---------|-------------|
| `CLAUDE.md` | Basic project information | Every conversation |
| `.claude/rules/doc-maintenance.md` | Documentation maintenance rules | When code files are modified |
| `.claude/rules/project-structure.md` | Project structure navigation | Every conversation |
