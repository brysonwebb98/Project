# F4 — Credit Information

## Metadata

- Feature ID: F4
- Severity: High
- Status: Missing
- Effort: Medium
- Depends on: Create Application

## 1. Problem

Users need to pull credit information into the application so the loan can later be reviewed and underwritten.

## 2. Goals

- Pull credit information from an external API.
- Display the credit report information in the application.
- Prevent users from manually editing the credit report.
- Require credit to be pulled before the application can be submitted.

## 3. Non-Goals

- Manually editing the credit report.
- Calculating financial ratios in this section.
- Updating underwriting information in this section.

## 4. User Story

As a Loan Officer or Credit Manager, I want to pull a credit report so that the applicant's credit information can be reviewed.

## 5. Functional Requirements

- FR-1: The system MUST pull credit information from an external API.
- FR-2: The system MUST store the returned credit information with the application.
- FR-3: Users MUST NOT be able to manually edit the credit report.
- FR-4: The system MUST allow an application to remain in `Draft` before credit is pulled.
- FR-5: The system MUST prevent submission until credit has been successfully pulled.
- FR-6: Credit information MAY later be updated through the underwriting process, but not directly inside the credit report.

## 6. Non-Functional Requirements

- Security: Credit information must only be available to authorized users.
- Reliability: Credit data should only be saved after a successful API response.
- Performance: The system should clearly show when the credit report is loading.

## 7. Acceptance Criteria

- AC-1: Given a valid application, when credit is successfully pulled, then the credit information is saved and displayed.
- AC-2: Given credit has not been pulled, when the user tries to submit the application, then submission is blocked.
- AC-3: Given credit information is displayed, when a user views it, then the report cannot be manually edited.
- AC-4: Given credit has not been pulled yet, when the user saves the application, then it can remain as a `Draft`.
- AC-5: Given the credit API fails, when credit is pulled, then an error is shown and the application remains in `Draft`.

## 8. Data

Credit information may include:

- Credit score
- Monthly debt payments
- Housing payment
- Other important credit information returned by the API

Income is not part of the credit report.

## 9. API

Possible routes:

- `POST /api/applications/:id/credit`
- External credit report API

The system sends the credit request and stores the returned information with the application.

## 10. UI

- Pull Credit button
- Loading state while credit is being retrieved
- Credit report display
- Credit score
- Monthly debts
- Housing payment
- Error message if the credit pull fails
- Read-only credit information

## 11. AI / ML

N/A — AI is not used for credit reporting.

## 12. Integration Points

- Application database
- External credit report API
- Authentication
- Underwriting workflow

## 13. Dependencies

Needs:

- Create Application
- External credit API

Unblocks:

- Submit Application
- Underwriting review

## 14. Risks

- Risk: The credit API fails or does not return data.
- Mitigation: Show an error and keep the application as a `Draft`.

## 15. Rollout

1. Connect to the credit API.
2. Add the Pull Credit action.
3. Save returned credit data.
4. Display the report as read-only.
5. Block submission until credit is pulled.

## 16. Test Plan

- AC-1: Test that a successful credit pull saves and displays the credit information.
- AC-2: Test that submission is blocked without a credit report.
- AC-3: Test that credit information cannot be manually edited.
- AC-4: Test that an application can remain in `Draft` before credit is pulled.
- AC-5: Test that a failed credit pull shows an error and keeps the application in `Draft`.

## 17. Open Questions

- Which external credit API will be used?