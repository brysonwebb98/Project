# F2 — Dashboard

## Metadata

- Feature ID: F2
- Severity: High
- Status: Missing
- Effort: Small
- Depends on: User Authentication

## 1. Problem

Users need one main place to see the work that belongs to them and quickly get to the next action they need to take.

## 2. Goals

- Give every user a main dashboard.
- Show information based on the user's role.
- Help users quickly access the work in their queue.

## 3. Non-Goals

- Advanced analytics.
- Complex reporting.
- Custom dashboards for each individual user.

## 4. User Story

As a user, I want to see the work assigned to my role so that I know what I need to do next.

## 5. Functional Requirements

- FR-1: The system MUST show a dashboard after login.
- FR-2: The system MUST change dashboard content based on the user's role.
- FR-3: Credit Managers MUST see applications that need a decision.
- FR-4: Admins MUST be able to access user management.
- FR-5: Loan Officers MUST be able to start a new application.
- FR-6: The system SHOULD show a message when there is nothing in the user's queue.

## 6. Non-Functional Requirements

- Security: Users should only see actions allowed for their role.
- Performance: Dashboard information should load quickly.
- Reliability: The correct queue should display for each user role.

## 7. Acceptance Criteria

- AC-1: Given a logged-in user, when the dashboard loads, then the user sees content for their role.
- AC-2: Given a Credit Manager, when the dashboard loads, then applications needing a decision are shown.
- AC-3: Given an Admin, when the dashboard loads, then user management can be accessed.
- AC-4: Given a Loan Officer, when the dashboard loads, then they can start a new application.
- AC-5: Given there is nothing in the user's queue, when the dashboard loads, then an empty message is shown.

## 8. Data

The dashboard may use:

- User role
- Applications
- Application status
- Assigned or created applications

## 9. API

Possible routes:

- `GET /api/dashboard`
- `GET /api/applications`

The system returns dashboard information based on the logged-in user's role.

## 10. UI

- Main dashboard page
- Application queue
- New Application option for Loan Officers
- User Management option for Admins
- Decision queue for Credit Managers
- Empty-state message such as "No applications yet" or "Take it easy."
- Loading state while dashboard information is being retrieved
- Error message if dashboard information fails to load

## 11. AI / ML

N/A — AI is not used for the dashboard.

## 12. Integration Points

- Authentication
- Applications
- User roles
- User management

## 13. Dependencies

Needs:

- User Authentication
- User roles

Unblocks:

- Application workflows
- Credit Manager review
- User management access

## 14. Risks

- Risk: Users see actions they are not authorized to use.
- Mitigation: Check user roles before showing dashboard actions.

## 15. Rollout

1. Create dashboard page.
2. Add role-based content.
3. Connect application queues.
4. Add empty states.
5. Test each user role.

## 16. Test Plan

- AC-1: Test that each logged-in user sees dashboard content for their role.
- AC-2: Test that Credit Managers see applications needing a decision.
- AC-3: Test that Admins can access user management.
- AC-4: Test that Loan Officers can start a new application.
- AC-5: Test that an empty-state message appears when there is nothing in the user's queue.
- Test that users cannot access dashboard actions outside their role.

## 17. Open Questions

- N/A