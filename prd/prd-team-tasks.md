# PRD: Team Tasks

## Introduction/Overview
Teams need a lightweight way to capture tasks, assign owners, set due dates, and track completion with comments and basic notifications.

## Goals
1. Enable teams to create, assign, and track tasks to completion.
2. Provide minimal friction for adoption (clear UX, fast interactions).
3. Deliver an MVP that supports comments and basic notifications.

## User Stories
1. As a team member, I can create a task with title, description, and due date.
2. As a team member, I can assign a task to a specific owner.
3. As a team member, I can mark a task as completed.
4. As a team member, I can comment on a task.
5. As a team member, I receive a basic notification when I’m assigned a task or when my task is commented on.

## Functional Requirements
1. Create Task: title (required), description (optional), due date (optional), assignee (optional on create), status defaults to "Open".
2. Assign Task: reassign ownership at any time.
3. Complete Task: mark status as "Done" and timestamp completion.
4. Comment on Task: add comment with author and timestamp.
5. Notifications: email (or in-app stub) on assignment and comment events.

## Acceptance Criteria
| # | Scenario | Expected Result |
|---|---|---|
| 1 | Create a task with title only | Task saved with status Open, no assignee, no due date |
| 2 | Assign a task to a user | Task shows new assignee, notification sent to assignee |
| 3 | Complete a task | Task status becomes Done with completedAt timestamp |
| 4 | Add a comment | Comment appears under task with author and timestamp |
| 5 | Comment triggers notification | Notification sent to task assignee |

## Non-Goals (Out of Scope)
- Advanced workflow (subtasks, labels, priorities)
- External integrations beyond basic email (no Slack for MVP)
- SSO and granular RBAC (basic role assumption only)

## Design Considerations (Optional)
- Keep UI minimal; emphasize list and detail view.

## Technical Considerations (Optional)
- Simple persistence layer (e.g., JSON or lightweight DB) for MVP.
- Basic mailer interface that can be stubbed in dev.

## Success Metrics
- 70% of created tasks are completed within 7 days in pilot teams
- < 1 minute median time to create and assign a task

## Open Questions
- Should comments support mentions (e.g., @user) in MVP?
- Should due date reminders be part of MVP notifications?

