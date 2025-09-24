## Relevant Files

- `app/tasks/TaskList.tsx` - Main task list UI.
- `app/tasks/TaskDetails.tsx` - Task detail view with comments.
- `app/tasks/api.ts` - Client API for tasks, comments, and notifications.
- `server/routes/tasks.ts` - API route handlers for tasks.
- `server/routes/comments.ts` - API route handlers for comments.
- `server/services/notifications.ts` - Notification service (email stub).
- `lib/db.ts` - Persistence adapter (MVP).
- `docs/test-coverage.md` - Test coverage report.

### Notes

- **Testing Strategy:** Follow TDD; write tests first for each sub-task.
- **Coverage Target:** Aim for 100% line coverage where practical.
- **Test Types:** Unit and integration tests for MVP.
- **Coverage Updates:** Update `docs/test-coverage.md` after each major task completion.

## Tasks

- [ ] 1.0 Backend MVP for Tasks
  - [ ] 1.1 Create task model and repository with CRUD operations
    - Write comprehensive tests following TDD approach
    - Run all tests and fix any failures
    - Generate coverage report and analyze gaps
    - Add tests to achieve target coverage
  - [ ] 1.2 Implement routes for create/list/update/status change
    - Write comprehensive tests following TDD approach
    - Run all tests and fix any failures
    - Generate coverage report and analyze gaps
    - Add tests to achieve target coverage
  - [ ] 1.3 Validate Task 1.0 completion
    - Run complete test suite (all tests must pass)
    - Generate final coverage report for Task 1.0
    - Update `docs/test-coverage.md` with Task 1.0 results
    - Verify all acceptance criteria are tested and covered

- [ ] 2.0 Comments and Notifications MVP
  - [ ] 2.1 Add comments endpoints and persistence
    - Write comprehensive tests following TDD approach
    - Run all tests and fix any failures
    - Generate coverage report and analyze gaps
    - Add tests to achieve target coverage
  - [ ] 2.2 Add basic notification service (assignment, comment)
    - Write comprehensive tests following TDD approach
    - Run all tests and fix any failures
    - Generate coverage report and analyze gaps
    - Add tests to achieve target coverage
  - [ ] 2.3 Validate Task 2.0 completion
    - Run complete test suite (all tests must pass)
    - Generate final coverage report for Task 2.0
    - Update `docs/test-coverage.md` with Task 2.0 results
    - Verify all acceptance criteria are tested and covered

- [ ] 3.0 Frontend MVP
  - [ ] 3.1 Task list and detail views with create/assign/complete/comment flows
    - Write comprehensive tests following TDD approach
    - Run all tests and fix any failures
    - Generate coverage report and analyze gaps
    - Add tests to achieve target coverage
  - [ ] 3.2 Validate Task 3.0 completion
    - Run complete test suite (all tests must pass)
    - Generate final coverage report for Task 3.0
    - Update `docs/test-coverage.md` with Task 3.0 results

