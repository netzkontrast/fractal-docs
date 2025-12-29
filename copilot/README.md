# GitHub Copilot Initialization Guide

## Core Concepts

- **INIT_PROMPT.md** = One-time initialization instructions (no longer needed after copying to chat)
- **Generated Rules** = Persistent configuration (loaded with each AI interaction)

## How to Use

1. Copy the content of `INIT_PROMPT.md` into the GitHub Copilot Chat
2. The AI will analyze your project and generate `.github/copilot-instructions.md`
3. After initialization, `INIT_PROMPT.md` is no longer needed

## What's Generated After Initialization

```
your-project/
├── .github/
│   └── copilot-instructions.md         # Project instructions (persistent)
└── [core-directory]/README.md          # Directory index (persistent)
```

## Explanation of Generated Rules

| File | Purpose | When Loaded |
|------|---------|-------------|
| `copilot-instructions.md` | Project instructions (including doc maintenance rules and project structure) | Every conversation |

## GitHub Copilot Features

- Only supports a single configuration file: `.github/copilot-instructions.md`
- Does not support conditional loading
- Does not support file reference syntax
