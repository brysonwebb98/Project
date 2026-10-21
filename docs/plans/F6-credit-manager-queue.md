# F6 — Credit Manager Queue

## Metadata

- Feature ID: F6
- Severity: High
- Status: Missing
- Effort: Small
- Depends on: Submit Application

## 1. Problem

Credit Managers need one place to see applications that are waiting for a decision.

## 2. Goals

- Show submitted applications in the Credit Manager queue.
- Show applications started by the Credit Manager.
- Make it easy to open an application for review.
- Sort applications from oldest to newest.
- Allow filtering.

## 3. Non-Goals

- Loan Officers viewing the Credit Manager queue.
- Admins viewing the Credit Manager queue.
- Making the final credit decision directly from the queue.

## 4. User Story

As a Credit Manager, I want to see applications waiting for review so that I can work through them in order.

## 5. Functional Requirements

- FR-1: The system MUST only allow Credit Managers to access the queue.
- FR-2: The queue MUST show submitted applications waiting for review.
- FR-3: The queue SHOULD also show applications started by the Credit Manager.
- FR-4: The queue MUST show applicant name, requested loan amount, Loan Officer, credit score, status, and date submitted.
- FR-5: Applications MUST be sorted from oldest to newest by default.
- FR-6: The system MUST allow the Credit Manager to filter the queue.
- FR-7: Selecting an application MUST open the application review screen.

## 6. Non-Functional Requirements

- Security: Only Credit Managers can access the queue.
- Performance: The queue should load quickly.
- Reliability: Submitted applications should appear correctly in the queue.

## 7. Acceptance Criteria

- AC-1: Given a Credit Manager, when the queue loads, then submitted applications are shown.
- AC-2: Given a non-Credit Manager, when they try to access the queue, then access is denied.
- AC-3: Given multiple submitted applications, when the queue loads, then they are sorted from oldest to newest.
- AC-4: Given a Credit Manager, when they select an application, then the full application review screen opens.
- AC-5: Given a Credit Manager, when they select a filter, then the queue updates to match the filter.
- AC-6: Given there are no submitted applications, when the queue loads, then an empty queue message is shown.

## 8. Data

Queue information includes:

- Applicant name
- Requested loan amount
- Loan Officer
- Credit score
- Application status
- Date submitted

## 9. API

Possible route:

- `GET /api/applications/submitted`

The route returns applications available for Credit Manager review.

## 10. UI

- Credit Manager queue
- Application list
- Filters
- Applicant name
- Loan amount
- Loan Officer
- Credit score
- Status
- Date submitted
- Empty queue message
- Loading state while applications are being retrieved
- Error message if the queue fails to load

## 11. AI / ML

N/A — AI is not used for the Credit Manager queue.

## 12. Integration Points

- Authentication
- Application database
- Submit Application
- Application Review

## 13. Dependencies

Needs:

- User Authentication
- Submit Application

Unblocks:

- Review & Decision

## 14. Risks

- Risk: Applications do not appear in the correct order.
- Mitigation: Sort by submission date by default.

## 15. Rollout

1. Create the Credit Manager queue.
2. Load submitted applications.
3. Add sorting.
4. Add filters.
5. Connect applications to the review screen.

## 16. Test Plan

- AC-1: Test that submitted applications appear for Credit Managers.
- AC-2: Test that non-Credit Managers cannot access the queue.
- AC-3: Test oldest-to-newest sorting.
- AC-4: Test that selecting an application opens the review screen.
- AC-5: Test that filters update the queue correctly.
- AC-6: Test that an empty queue message appears when there are no submitted applications.
- Test that a loading state and error message display correctly.

## 17. Open Questions

- Which specific filters should be included?