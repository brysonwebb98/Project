# 1.1 — Submit Loan Application

> Implementation plan for allowing a loan officer to submit a completed loan application for review.

## Metadata

| Field | Value |
|---|---|
| **Feature ID** | 1.1 |
| **Section** | Loan Application Workflow |
| **Severity** | BLOCKER |
| **Markets** | Financial Institutions |
| **Status (today)** | MISSING |
| **Estimated effort** | XS (≤1d) |
| **Owner (proposed)** | Bryson Webb / Development Team |
| **Depends on** | User Authentication, Existing Draft Application |
| **Unblocks** | Credit Manager Queue, Application Review |

---

## 1. Problem Statement

Loan officers need a way to send a completed draft application forward for review without all of the extra fluff that is added within old banking systems. The goal is to make submission simple, fast, and focused only on the information needed for review.

## 2. Goals

- Allow a loan officer to submit a completed draft application.
- Keep the submission process simple.
- Validate required information before submission.
- Change the application status to `Submitted`.
- Record when the application was submitted.

## 3. Non-Goals

- Automatic underwriting.
- Credit bureau integration.
- Document uploads.
- Approval conditions.
- Extra submission steps that are not needed for review.

## 4. Personas & User Stories

- As a loan officer, I want to submit a completed application quickly so that it can move to credit review without unnecessary steps.

## 5. Functional Requirements

- **FR-1.** The system MUST allow a loan officer to submit a draft application.
- **FR-2.** The system MUST check required fields before submission.
- **FR-3.** The system MUST prevent submission if required information is missing.
- **FR-4.** The system MUST change the status from `Draft` to `Submitted`.
- **FR-5.** The system MUST record the submission date.
- **FR-6.** The system MUST keep the application as `Draft` if submission fails.

## 6. Non-Functional Requirements

- **Performance** — Submission should complete quickly under normal use.
- **Security** — Only an authenticated loan officer should be able to submit.
- **Reliability** — Status should only change after a successful save.
- **Accessibility** — The submit button and validation messages should be clear and keyboard accessible.
- **Maintainability** — Submission logic should follow the existing project structure.

## 7. Acceptance Criteria

- **AC-1.** Given a completed draft application, when the loan officer selects Submit Application, then the application is submitted.
- **AC-2.** Given required information is missing, when submission is attempted, then the application stays in `Draft`.
- **AC-3.** Given submission succeeds, when the application is saved, then the status changes to `Submitted`.
- **AC-4.** Given submission succeeds, then the submission date is recorded.
- **AC-5.** Given submission fails, then the application remains in `Draft`.

## 8. Data Model

The application must contain the required information before it can be submitted.

Applicant information:

- First name
- Last name
- Phone number
- Email
- Address
- Housing status
- Monthly housing payment

Employment and income:

- Employer name
- Job title
- Employment status
- Monthly or annual income

Loan information:

- Requested loan amount
- Loan purpose

Credit information:

- Credit score
- Monthly debt payments

Submission fields:

- `status`
- `dateSubmitted`

Status change:

- `Draft` → `Submitted`

No new tables are required for this feature.

## 9. API Surface

Route:

`POST /api/applications/:id/submit`

Requirements:

- User must be authenticated.
- User must be a Loan Officer.
- Application must be in `Draft`.
- Required fields must be complete.

Successful result:

- Status becomes `Submitted`.
- Submission date is saved.

## 10. UI / UX

UI:

- `Submit Application` button.
- Validation messages for missing information.
- Loading state while submitting.
- Success message after submission.
- Error message if submission fails.

Flow:

1. Loan officer opens a draft application.
2. Selects `Submit Application`.
3. System validates required information.
4. Application is submitted.
5. Status changes to `Submitted`.

## 11. AI / ML Considerations

N/A — AI is not used for application submission.

## 12. Integration Points

Internal:

- Authentication
- User roles
- Application database

External:

- N/A

## 13. Dependencies & Sequencing

Must already exist:

- User authentication
- Loan Officer role
- Draft application
- Application database

Unblocks:

- Credit Manager Queue
- Application Review

## 14. Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| Required data is missing | M | M | Validate before submission |
| Unauthorized user submits | L | H | Check user role |
| Submission fails | L | H | Keep status as `Draft` |
| Submission becomes too complex | M | M | Keep only required steps |

## 15. Rollout Plan

1. Add submission validation.
2. Add the submit API route.
3. Add the Submit Application button.
4. Connect the UI to the API.
5. Test successful and failed submissions.

Feature flag: N/A

Rollback: Revert the submission changes through source control.

## 16. Test Plan

**Unit**

- Required field validation.
- Draft to Submitted status change.

**Integration**

- Submit a valid draft.
- Reject an incomplete draft.
- Save the submission date.
- Keep Draft status after failure.

**Security**

- Reject unauthenticated users.
- Reject users without the Loan Officer role.

**UI**

- Submit button works.
- Loading state appears.
- Validation errors appear.
- Success and error messages display correctly.