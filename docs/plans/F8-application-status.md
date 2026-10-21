# F8 — Application Status

## Metadata

- Feature ID: F8
- Severity: High
- Status: Missing
- Effort: Small
- Depends on: Submit Application, Review & Decision

## 1. Problem

Loan Officers and Credit Managers need to quickly see where each application is in the loan process.

## 2. Goals

- Show the current application status on the dashboard and queues.
- Keep application statuses updated as the loan moves through the process.
- Allow authorized users to update status when needed.

## 3. Non-Goals

- Admins managing application statuses.
- Automatic underwriting decisions.

## 4. User Story

As a Loan Officer or Credit Manager, I want to see an application's status so that I know where it is in the process.

## 5. Functional Requirements

- FR-1: The system MUST display application status on the dashboard or queue.
- FR-2: The system MUST support `Submitted`, `Pending`, `Approved`, `Counter`, and `Denied`.
- FR-3: Loan Officers and Credit Managers MUST be able to view application status.
- FR-4: Credit Managers MUST be able to update decision statuses.
- FR-5: Loan Officers MUST NOT approve, counter, or deny applications.

## 6. Non-Functional Requirements

- Security: Status changes must follow user permissions.
- Reliability: Status changes must be saved correctly.
- Performance: Status should display when the queue loads.

## 7. Acceptance Criteria

- AC-1: Given a Loan Officer or Credit Manager, when they view their queue, then the current application status is shown.
- AC-2: Given a Credit Manager makes a decision, when it is saved, then the status updates.
- AC-3: Given a Loan Officer, when they view an application, then they can see the status but cannot make a credit decision.
- AC-4: Given a status update fails, when the change is attempted, then the current status remains unchanged and an error message is shown.

## 8. Data

Application status can be:

- `Submitted`
- `Pending`
- `Approved`
- `Counter`
- `Denied`

## 9. API

Possible route:

- `PUT /api/applications/:id/status`

The route updates the application status based on user permissions.

## 10. UI

- Status displayed on dashboard and queue
- Status shown beside each application
- Status controls for authorized Credit Managers
- Loading state while status information is being retrieved
- Error message if a status update fails

## 11. AI / ML

N/A — AI is not used for application status.

## 12. Integration Points

- Dashboard
- Credit Manager Queue
- Submit Application
- Review & Decision

## 13. Dependencies

Needs:

- Submit Application
- Review & Decision

Unblocks:

- N/A

## 14. Risks

- Risk: Unauthorized users change a loan decision.
- Mitigation: Restrict decision statuses to Credit Managers.

## 15. Rollout

1. Add application statuses.
2. Display status on queues.
3. Add status update permissions.
4. Test each status.

## 16. Test Plan

- AC-1: Test that application status displays on the dashboard and queue.
- AC-2: Test that Credit Manager decisions update the application status.
- AC-3: Test that Loan Officers can view status but cannot make credit decisions.
- AC-4: Test that a failed status update shows an error and keeps the current status unchanged.
- Test each supported application status.

## 17. Open Questions

- N/A