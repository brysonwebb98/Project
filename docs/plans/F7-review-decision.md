# F7 — Review & Decision

## Metadata

- Feature ID: F7
- Severity: High
- Status: Missing
- Effort: Medium
- Depends on: Credit Manager Queue

## 1. Problem

Credit Managers need a simple way to review submitted applications and make a credit decision.

## 2. Goals

- Allow Credit Managers to review the full submitted application.
- Show all important applicant, income, credit, ratio, and note information.
- Allow the Credit Manager to make a decision.
- Update the application status after the decision.

## 3. Non-Goals

- Loan Officers making final credit decisions.
- Admins making final credit decisions.
- Advanced automated underwriting.

## 4. User Story

As a Credit Manager, I want to review a submitted application and make a decision so that the loan can move forward.

## 5. Functional Requirements

- FR-1: The system MUST only allow Credit Managers to make credit decisions.
- FR-2: The system MUST show applicant information, employment and income, credit information, ratios, and Loan Officer notes.
- FR-3: The Credit Manager MUST be able to add notes.
- FR-4: The Credit Manager MUST be able to choose `Approved`, `Counter`, `Denied`, or `Pending`.
- FR-5: The system MUST update the application status after the decision is saved.

## 6. Non-Functional Requirements

- Security: Only Credit Managers can make decisions.
- Reliability: The decision and notes should save correctly.
- Performance: The review screen should load application information quickly.

## 7. Acceptance Criteria

- AC-1: Given a submitted application, when a Credit Manager opens it, then all application information is shown.
- AC-2: Given a Credit Manager, when they add notes and save them, then the notes are saved with the application.
- AC-3: Given a Credit Manager selects a decision, when they save it, then the application status is updated.
- AC-4: Given a non-Credit Manager, when they try to make a decision, then access is denied.
- AC-5: Given the review screen fails to load or save, when an error occurs, then an error message is shown.

## 8. Data

The review screen uses:

- Applicant information
- Employment and income
- Credit information
- Financial ratios
- Loan Officer notes
- Credit Manager notes
- Application status
- Decision date

Possible statuses:

- `Approved`
- `Counter`
- `Denied`
- `Pending`

## 9. API

Possible routes:

- `GET /api/applications/:id`
- `POST /api/applications/:id/decision`
- `POST /api/applications/:id/notes`

These routes load the application, save notes, and save the decision.

## 10. UI

- Full application review screen
- Applicant information
- Employment and income
- Credit information
- Ratios
- Loan Officer notes
- Credit Manager notes field
- Approve button
- Counter button
- Deny button
- Pending button
- Loading state while application information is being retrieved
- Error message if application information, notes, or a decision fails to save

## 11. AI / ML

N/A — AI is not used for credit decisions.

## 12. Integration Points

- Credit Manager Queue
- Application database
- Credit information
- Application notes
- Application status

## 13. Dependencies

Needs:

- Credit Manager Queue
- Submitted application
- Credit information

Unblocks:

- Application Status

## 14. Risks

- Risk: The wrong user makes a credit decision.
- Mitigation: Restrict decision actions to Credit Managers.

## 15. Rollout

1. Create the review screen.
2. Load all application information.
3. Add Credit Manager notes.
4. Add decision options.
5. Update the application status.

## 16. Test Plan

- AC-1: Test that submitted application information displays correctly.
- AC-2: Test that Credit Manager notes save correctly.
- AC-3: Test `Approved`, `Counter`, `Denied`, and `Pending` decisions update the application status.
- AC-4: Test that non-Credit Managers cannot make credit decisions.
- AC-5: Test that an error message appears if loading or saving fails.

## 17. Open Questions

- N/A