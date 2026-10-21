# F5 — Submit Application

## Metadata

- Feature ID: F5
- Severity: High
- Status: Missing
- Effort: Small
- Depends on: Create Application, Credit Information

## 1. Problem

Loan Officers need a simple way to send a completed application to a Credit Manager for review.

## 2. Goals

- Allow Loan Officers to submit completed applications.
- Require the application to be fully filled out.
- Require credit to be pulled before submission.
- Move submitted applications into `Submitted` status for Credit Manager review.

## 3. Non-Goals

- Credit Managers submitting applications.
- Approving or denying applications in this feature.
- Editing applications while they are in `Submitted` status.

## 4. User Story

As a Loan Officer, I want to submit a completed application so that a Credit Manager can review it.

## 5. Functional Requirements

- FR-1: The system MUST allow Loan Officers to submit applications.
- FR-2: The application MUST be fully completed before submission.
- FR-3: Credit MUST be pulled before submission.
- FR-4: The system MUST change the application status to `Submitted` after successful submission.
- FR-5: The system MUST prevent editing while the application is in `Submitted` status.
- FR-6: If submission fails, the application MUST remain in `Draft` status.

## 6. Non-Functional Requirements

- Security: Only Loan Officers can submit applications.
- Reliability: Status should only change after successful submission.
- Performance: Submission should complete quickly.

## 7. Acceptance Criteria

- AC-1: Given a completed application with credit pulled, when the Loan Officer submits it, then the status changes to `Submitted`.
- AC-2: Given required information is missing, when submission is attempted, then submission is blocked.
- AC-3: Given credit has not been pulled, when submission is attempted, then submission is blocked.
- AC-4: Given an application is `Submitted`, when a user opens it, then application information cannot be edited.
- AC-5: Given submission fails, when the Loan Officer attempts to submit the application, then the application remains in `Draft`.

## 8. Data

Submission uses:

- Application status
- Required application fields
- Credit report status
- Submission date

Status change:

- `Draft` → `Submitted`

## 9. API

Possible route:

- `POST /api/applications/:id/submit`

The route validates the application and moves it into `Submitted` status.

## 10. UI

- Submit Application button
- Validation message for missing information
- Validation message if credit has not been pulled
- Loading state during submission
- Success message after submission
- Error message if submission fails

## 11. AI / ML

N/A — AI is not used for application submission.

## 12. Integration Points

- Application database
- Credit information
- Credit Manager queue
- Authentication

## 13. Dependencies

Needs:

- Create Application
- Credit Information

Unblocks:

- Credit Manager Queue
- Application Review

## 14. Risks

- Risk: An incomplete application gets submitted.
- Mitigation: Validate required information and credit before submission.

## 15. Rollout

1. Add submission validation.
2. Add submit route.
3. Change successful submissions to `Submitted`.
4. Lock Submitted applications from editing.
5. Test successful and failed submissions.

## 16. Test Plan

- AC-1: Test a successful submission with a completed application and credit pulled.
- AC-2: Test submission with missing application data.
- AC-3: Test submission without credit.
- AC-4: Test that `Submitted` applications cannot be edited.
- AC-5: Test that a failed submission keeps the application in `Draft`.

## 17. Open Questions

- N/A