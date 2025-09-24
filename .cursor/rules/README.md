# Cursor Rules

This folder contains project-specific rules (`.mdc`) that guide Cursor's AI.

## How it works
- Cursor loads `.mdc` files recursively from this directory (including subfolders).
- Each rule uses YAML frontmatter to define scope and behavior.
- Use `globs` to target project files and `alwaysApply` for always-on rules.

## Current structure

```
.cursor/rules
├─ README.md
├─ general/
│  ├─ docs.mdc
│  └─ git.mdc
└─ product-dev/
   ├─ create-implementation-plan.mdc
   ├─ create-product-requirements.mdc
   └─ process-implementation-plan.mdc
```

## Generated artifacts
- Implementation plans are saved under `/impl-plan/` as `impl-plan-[prd-file-name].md`.

## File naming
- Use kebab-case for rule files.

## Frontmatter fields
- `description` (string): what the rule governs
- `globs` (string[]): project file patterns the rule applies to
- `alwaysApply` (boolean): load this rule automatically

## Key rules
- `product-dev/create-implementation-plan.mdc` – generate implementation plans from PRDs → `/impl-plan/impl-plan-[prd-file-name].md`
- `product-dev/process-implementation-plan.mdc` – maintain and update the implementation plan during execution
- `product-dev/create-product-requirements.mdc` – generate PRDs from prompts/clarifications
- `general/docs.mdc` – documentation standards for READMEs, ADRs, and comments
- `general/git.mdc` – git hygiene and workflow for branches, commits, and PRs

## Tips
- Keep rules concise and actionable
- Prefer examples over prose
- Split language/tool/ecosystem rules into separate files or subfolders

