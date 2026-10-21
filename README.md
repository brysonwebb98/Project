# Feature Plan Sequence

## Recommended Implementation Order

| Order | Feature | Depends On | Why |
|---|---|---|---|
| 1 | F1 - User Authentication | None | Users need to log in before accessing the system. |
| 2 | F9 - User Management | F1 | Admins need to create users and assign roles. |
| 3 | F2 - Dashboard | F1 | Gives users a main place to access their work. |
| 4 | F3 - Create Application | F1 | Loan Officers and Credit Managers need to create applications. |
| 5 | F4 - Credit Information | F3 | Credit must be connected to an existing application. |
| 6 | F5 - Submit Application | F3, F4 | Applications must be completed and have credit pulled before submission. |
| 7 | F6 - Credit Manager Queue | F5 | Submitted applications need to appear for Credit Managers. |
| 8 | F7 - Review & Decision | F6 | Credit Managers need to open submitted applications and make decisions. |
| 9 | F8 - Application Status | F5, F7 | Status changes are based on submission and credit decisions. |

## Dependency Map

- F1 unlocks most of the application.
- F3 must exist before credit information can be added.
- F4 must be completed before an application can be submitted.
- F5 must exist before applications can appear in the Credit Manager queue.
- F6 must exist before Credit Managers can review applications.
- F7 updates the application status after a decision.

## First Feature to Implement

The first feature should be **User Authentication** because users need to log in before using the rest of the system. Authentication also allows the application to control what Loan Officers, Credit Managers, and Admins are allowed to access.

## Risks That Could Delay Multiple Features

- Authentication or role permissions not working correctly.
- The credit API taking longer than expected to integrate.
- Application data not saving correctly.
- Status changes not staying consistent between the dashboard, queue, and review screen.