# Cursor Product Development Guide

A lightweight guide and rule set for running product development with AI assistance in Cursor.

## Goals
- Provide clear, repeatable steps to go from a product idea to a shippable plan.
- Standardize artifacts: PRDs and Implementation Plans in predictable locations.
- Encode process rules so Cursor can assist reliably during execution.

## Repository Structure

```
.
├─ README.md                      # This file
├─ .cursor/
│  └─ rules/
│     ├─ README.md                # Rules index and guidance
│     ├─ general/
│     │  ├─ docs.mdc              # Documentation standards
│     │  └─ git.mdc               # Git hygiene & workflow
│     └─ product-dev/
│        ├─ create-product-requirements.mdc     # Generate PRDs from prompts
│        ├─ create-implementation-plan.mdc      # Generate implementation plan from a PRD
│        └─ process-implementation-plan.mdc     # Maintain the plan during execution
├─ prd/                           # Generated PRDs
│  └─ prd-[feature-name].md
└─ impl-plan/                     # Generated implementation plans
   └─ impl-plan-[prd-file-name].md
```

## How Cursor Uses These Rules
- Cursor recursively loads `.mdc` rule files from `.cursor/rules/` (including subfolders).
- Each rule includes YAML frontmatter with a description, globs, and whether it should always apply.
- The rules guide AI behavior for authoring PRDs, implementation plans, and maintaining progress.

## Product Development Flow
The core flow uses three rules in the `product-dev` folder.

```mermaid
flowchart LR
  A[Prompt/Feature Idea] --> B(@product-dev/create-product-requirements.mdc)
  B -->|Output: prd-[feature-name].md| C(@product-dev/create-implementation-plan.mdc)
  C -->|Output: impl-plan-[prd-file-name].md| D(@product-dev/process-implementation-plan.mdc)
  D -->|Iterate: mark tasks, update files| D
```

### 1) Create a PRD
- Rule: `product-dev/create-product-requirements.mdc`
- Output: `/prd/prd-[feature-name].md`

What you do:
1. Provide a short feature prompt.
2. Answer the assistant’s clarifying questions.
3. The assistant generates a PRD and saves it in `/prd/`.

### 2) Create an Implementation Plan
- Rule: `product-dev/create-implementation-plan.mdc`
- Output: `/impl-plan/impl-plan-[prd-file-name].md`

What you do:
1. Point the assistant to your PRD file.
2. The assistant generates high‑level tasks first and pauses for your “Go”.
3. On "Go", it expands each parent task into actionable sub‑tasks and lists relevant files.

### 3) Execute and Maintain the Plan
- Rule: `product-dev/process-implementation-plan.mdc`
- What happens:
  - Work one sub‑task at a time.
  - After finishing a sub‑task, update the plan: change `[ ]` to `[x]` for the sub‑task (and parent when all subtasks are complete).
  - Keep the "Relevant Files" section current.
  - Pause after each sub‑task and wait for approval before starting the next.

## Test Workflow (Simulated Example)
Hypothetical product: "Team Tasks"

### Step A: Generate a PRD
Assistant: “Please provide a brief feature prompt.”

Your prompt:
```text
Build a Team Tasks feature so teams can create tasks, assign owners, set due dates, and track completion. Must support comments and basic notifications.
```

Assistant asks clarifying questions (examples):
```text
- Who is the primary user segment?
- Which roles/permissions exist (admin, member)?
- What are the must-have actions for v1?
- Any external integrations (email, Slack)?
- Non-goals for v1?
- Success metrics for launch?
```

You answer briefly. Assistant creates and saves:
- `/prd/prd-team-tasks.md`

### Step B: Generate an Implementation Plan
You say:
```text
Use the PRD at /prd/prd-team-tasks.md to generate the implementation plan.
```
Assistant produces high-level tasks (parent tasks only) and says it is ready to expand. You reply:
```text
Go
```
Assistant expands into sub‑tasks, adds a "Relevant Files" section, and saves:
- `/impl-plan/impl-plan-prd-team-tasks.md`

### Step C: Execute with Check‑off Protocol
For each sub‑task:
1. Implement the change.
2. Update `/impl-plan/impl-plan-prd-team-tasks.md`:
   - Mark the sub‑task `[x]`.
   - If all sub‑tasks under a parent are `[x]`, mark the parent `[x]`.
   - Update "Relevant Files" with any new/changed files and one‑line purposes.
3. Stop and wait for approval before beginning the next sub‑task.

Example sub‑task approval loop:
```text
Assistant: Sub-task 1.2 complete. Marked [x]. Ready for 1.3? (yes/no)
You: yes
```

## Conventions
- PRDs live in `/prd/prd-[feature-name].md`.
- Implementation plans live in `/impl-plan/impl-plan-[prd-file-name].md`.
- Keep rule files small and focused; organize by domain under `.cursor/rules/`.

## Troubleshooting
- If artifacts are not being created, confirm the rule paths and filenames in `.mdc` frontmatter and body.
- Ensure you point the assistant to the correct PRD path when generating an implementation plan.
- If sub‑task pauses are skipped, reiterate the approval protocol from `process-implementation-plan.mdc`.
