# Fractal Docs

<p align="center">
  <img src="images/banner.jpeg" alt="Fractal Docs" width="600">
</p>

<p align="center">
  <strong>🌀 Let AI coding assistants automatically understand your project structure</strong>
</p>

---

## What is this?

Fractal Docs is a **self-maintaining documentation system** that enables AI coding assistants to:
- Automatically understand your project structure
- Automatically maintain documentation when modifying code
- Prevent overwriting existing documentation content

The design is inspired by the concepts of self-reference and recursion from "Gödel, Escher, Bach".

## Supported Editors

| Editor | Initialization Method | Generated Persistent Configuration |
|---|---|---|
| **Kiro** | Execute Spec | `.kiro/steering/` + `.kiro/templates/` |
| **Claude Code**| Copy INIT_PROMPT to chat | `CLAUDE.md` + `.claude/rules/` |
| **Cursor** | Copy INIT_PROMPT to chat | `.cursor/rules/*.mdc` |
| **Windsurf** | Copy INIT_PROMPT to chat | `.windsurf/rules/` |
| **Cline** | Copy INIT_PROMPT to chat | `.clinerules/` |
| **GitHub Copilot**| Copy INIT_PROMPT to chat | `.github/copilot-instructions.md` |

## Quick Start

### 1. Choose Your Editor

```bash
git clone https://github.com/wordflowlab/fractal-docs.git
```

### 2. Initialize Based on Your Editor

#### Kiro (Recommended)

```bash
# Copy the Spec to your project
cp -r fractal-docs/kiro/.kiro/specs/fractal-docs your-project/.kiro/specs/

# Open tasks.md in Kiro and let the AI execute it
```

#### Claude Code

```bash
# Copy the content of INIT_PROMPT.md to the Claude Code chat
cat fractal-docs/claude-code/INIT_PROMPT.md
```

#### Cursor

```bash
# Copy the content of INIT_PROMPT.md to the Cursor chat
cat fractal-docs/cursor/INIT_PROMPT.md
```

#### Windsurf / Cline / Copilot

Same as above, copy the content of `INIT_PROMPT.md` from the corresponding directory to the chat.

### 3. AI Executes Initialization

The AI will:
1. Analyze your project structure
2. Ask for core directories and language preference
3. Generate adapted configuration files
4. Create README.md for the core directories

### 4. Done

After that, every time the AI modifies the code, it will automatically maintain the documentation.

## Project Structure

```
fractal-docs/
├── kiro/                    # Kiro configuration (Spec method)
│   └── .kiro/specs/fractal-docs/
├── claude-code/             # Claude Code configuration
│   ├── README.md
│   └── INIT_PROMPT.md
├── cursor/                  # Cursor configuration
│   ├── README.md
│   └── INIT_PROMPT.md
├── windsurf/                # Windsurf configuration
├── cline/                   # Cline configuration
├── copilot/                 # GitHub Copilot configuration
└── templates/               # General template reference
    └── en/                  # English templates
```

## Core Features

- **🔄 Self-maintaining** - Documents contain self-referential reminders, triggering the AI to automatically update related documents
- **📁 Fractal Structure** - Each directory follows the same pattern: architecture description + file index
- **🛡️ Incremental Updates** - "Read before write" rule prevents accidental overwrites
- **🤖 Multi-editor** - Supports mainstream AI editors
- **🌍 Bilingual** - Supports Chinese and English

## What's Generated After Initialization?

Taking Kiro as an example:

```
your-project/
├── .kiro/
│   ├── steering/
│   │   ├── doc-maintenance.md    # Documentation maintenance rules (persistent)
│   │   └── project-structure.md  # Project structure navigation (persistent)
│   └── templates/
│       ├── folder-readme.md      # Folder README template
│       └── file-header-*.txt     # File header comment template
└── [core-directory]/README.md    # Directory index (persistent)
```

## Comparison of Editor Features

| Feature | Kiro | Claude Code | Cursor | Windsurf |
|---|---|---|---|---|
| File Reference | `#[[file:path]]` | `@path` | `@filename` | ❌ |
| Conditional Loading| `inclusion: fileMatch` | `paths` field | `globs` | Glob pattern |
| Modular Rules | `.kiro/steering/` | `.claude/rules/` | `.cursor/rules/` | `.windsurf/rules/` |
| Spec System | ✅ | ❌ | ❌ | ❌ |

## License

MIT

---

<p align="center">
  <sub>Inspired by <em>"Gödel, Escher, Bach: An Eternal Golden Braid"</em></sub>
</p>
