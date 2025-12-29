# Requirements Document

## Introduction

Fractal Docs is a documentation maintenance specification based on the Kiro Steering mechanism. It achieves fractal-structured document management through auto-loading rule files and file reference syntax. The system enables automatic documentation maintenance through standardized document templates and self-referential update reminders.

The design is inspired by the concepts of self-reference and recursion from "Gödel, Escher, Bach".

## Glossary

- **Steering**: Kiro's rule-loading mechanism, which automatically injects context via `.kiro/steering/*.md` files.
- **File Reference**: Kiro's `#[[file:path]]` syntax, which automatically fetches the content of the specified file into the context.
- **Fractal Structure**: A recursive structure where each level follows the same documentation pattern.
- **Self-referential Reminder**: Update reminder text within a document that triggers the AI to automatically maintain related documents.
- **Three-line Comment**: The standard input/output/pos comment format at the beginning of each file.
- **Inclusion Mode**: The loading method for Steering files (always/fileMatch/manual).

## Requirements

### Requirement 1: Kiro Steering Rule Configuration

**User Story:** As a developer, I want to automatically load documentation maintenance rules through the Kiro Steering mechanism.

#### Acceptance Criteria

1. The Steering system automatically loads rule files from the `.kiro/steering/` directory.
2. When a rule file is set to `inclusion: always`, it is loaded with every interaction.
3. When a rule file uses the `#[[file:path]]` syntax, the content of the referenced file is automatically fetched.
4. When the AI modifies a code file, the Steering rules prompt the execution of documentation maintenance steps.

### Requirement 2: Standardized Document Templates

**User Story:** As a developer, I want standardized document templates.

#### Acceptance Criteria

1. Folder README.md files use the standard architecture description + file index format.
2. File header comments use the standard input/output/pos format.
3. Update reminders use the standard self-referential reminder text.
4. Different file types use the corresponding language's comment format.

### Requirement 3: Project Structure Navigation

**User Story:** As a developer, I want the AI to quickly understand the project structure.

#### Acceptance Criteria

1. The Steering system automatically loads the README.md of core directories through file references.
2. The directory index provides a mapping between file names and feature descriptions.
3. When creating a new file, the directory index provides a reference for naming conventions.

### Requirement 4: Fractal Structure Self-Maintenance

**User Story:** As a developer, I want the documentation system to be self-maintaining through a self-referential mechanism.

#### Acceptance Criteria

1. Documents contain self-referential reminders to update related documents.
2. When the folder structure changes, the AI automatically updates the README.md of the current and parent directories.
3. When a new file is added, the AI automatically updates the file index of the parent folder.
4. When a code file is modified, the AI automatically updates the header comment of the file.

### Requirement 5: Incremental Update Protection

**User Story:** As a developer, I want the AI to read existing content before incrementally updating documents.

#### Acceptance Criteria

1. When updating a README.md, the AI first checks if the file exists.
2. If the README.md already exists, it is read before being incrementally updated.
3. If the README.md does not exist, it is created from a template.
4. When updating a file header comment, the existing comment is preserved and updated.

### Requirement 6: Documentation Maintenance Report

**User Story:** As a developer, I want the AI to output a documentation maintenance report after completing code modifications.

#### Acceptance Criteria

1. When code modifications are complete, the AI outputs a standard-format documentation maintenance report.
2. The report includes a list of modified files and their statuses.
3. The report includes the update status of README.md files.
4. The report includes the results of the parent directory check.
