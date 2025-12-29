# Kiro Initialization Guide

## Core Concepts

- **Spec** = One-time initialization task (no longer needed after execution)
- **Generated Steering** = Persistent configuration (loaded with each AI interaction)

## How to Use

1. Copy `.kiro/specs/fractal-docs/` to your project
2. Open `tasks.md` in Kiro
3. Let the AI execute the tasks in the Spec
4. After initialization, you can delete the `specs/fractal-docs/` directory

## What's Generated After Initialization

```
your-project/
├── .kiro/
│   ├── steering/
│   │   ├── doc-maintenance.md          # Documentation maintenance rules (persistent)
│   │   └── project-structure.md        # Project structure navigation (persistent)
│   └── templates/
│       ├── folder-readme.md            # Folder README template
│       └── file-header-*.txt           # File header comment template
└── [core-directory]/README.md          # Directory index (persistent)
```

## Explanation of Generated Rules

| File | Purpose | When Loaded |
|------|---------|-------------|
| `doc-maintenance.md` | Documentation maintenance rules | Every conversation (inclusion: always) |
| `project-structure.md` | Project structure navigation | Every conversation (inclusion: always) |
| `templates/` | Document templates | Referenced via `#[[file:path]]` |

## Kiro Features

- Supports the Spec system (structured task execution)
- Supports `#[[file:path]]` file reference syntax
- Supports `inclusion: fileMatch` for conditional loading
- Steering files are automatically loaded into the context
