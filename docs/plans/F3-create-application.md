# F3 — Create Application

## Metadata

- Feature ID: F3
- Severity: High
- Status: Missing
- Effort: Medium
- Depends on: User Authentication

## 1. Problem

Loan Officers and Credit Managers need a simple way to create a new loan application and enter all required applicant information.

## 2. Goals

- Allow Loan Officers and Credit Managers to create applications.
- Collect all required applicant and loan information.
- Save completed applications as drafts.
- Allow drafts to be edited before submission.

## 3. Non-Goals

- Admins creating applications.
- Submitting the application for a decision.
- Making an approval or denial decision.

## 4. User Story

As a Loan Officer or Credit Manager, I want to create a loan application so that I can collect the information needed for review.

## 5. Functional Requirements

- FR-1: The system MUST allow Loan Officers and Credit Managers to create applications.
- FR-2: The system MUST collect applicant name, contact information, address, employment, income, housing information, requested loan amount, and loan purpose.
- FR-3: The system MUST save a completed application as a `Draft`.
- FR-4: The system MUST allow users to edit a saved draft.
- FR-5: The system MUST warn users if they try to leave before enough information is entered to save.
- FR-6: The system MUST allow the user to either continue entering information or leave and lose unsaved data.

## 6. Non-Functional Requirements

- Security: Only Loan Officers and Credit Managers can create applications.
- Performance: Application forms should save quickly.
- Reliability: Incomplete unsaved applications should not create incomplete records.

## 7. Acceptance Criteria

- AC-1: Given a Loan Officer or Credit Manager, when they create an application and complete the required information, then the application can be saved as a `Draft`.
- AC-2: Given an Admin, when they try to create an application, then access is denied.
- AC-3: Given an incomplete unsaved application, when the user tries to leave, then a warning appears.
- AC-4: Given a saved draft, when the user returns later, then they can continue editing it.

## 8. Data

Application information includes:

- First and last name
- Phone number
- Email
- Address
- Employment information
- Income
- Housing status
- Monthly housing payment
- Requested loan amount
- Loan purpose
- Status

New applications are saved with the status:

- `Draft`

## 9. API

Possible routes:

- `POST /api/applications`
- `PUT /api/applications/:id`

These routes create and update draft applications.

## 10. UI

- New Application form
- Applicant information fields
- Employment and income fields
- Housing information
- Loan amount and purpose
- Save Draft button
- Loading state while saving
- Error message if saving fails
- Warning message when leaving with unsaved information

## 11. AI / ML

N/A — AI is not used for creating applications.

## 12. Integration Points

- Authentication
- User roles
- Application database

## 13. Dependencies

Needs:

- User Authentication
- User roles
- Application database

Unblocks:

- Credit Information
- Submit Application

## 14. Risks

- Risk: A user leaves before saving and loses their information.
- Mitigation: Show a warning before leaving an incomplete application.

## 15. Rollout

1. Create the application form.
2. Add required fields.
3. Add create and update routes.
4. Add draft saving.
5. Add the unsaved-data warning.

## 16. Test Plan

- AC-1: Test creating and saving an application as a Loan Officer and Credit Manager.
- AC-2: Test that Admins cannot create applications.
- AC-3: Test that a warning appears when leaving an incomplete unsaved application.
- AC-4: Test that a saved draft can be reopened and edited.
- Test that a failed save shows an error message.

## 17. Open Questions

- N/A