# F1 — User Authentication

## Metadata

- Feature ID: F1
- Severity: Blocker
- Status: Missing
- Effort: Small
- Depends on: None

## 1. Problem

Users need a secure way to log in before accessing the loan application system.

## 2. Goals

- Allow users to log in with email and password.
- Allow Loan Officers, Credit Managers, and Admins to log in.
- Send users to the dashboard after login.

## 3. Non-Goals

- Social media login.
- Multi-factor authentication.

## 4. User Story

As a user, I want to log in so that I can access the loan application system.

## 5. Functional Requirements

- FR-1: The system MUST allow users to log in with an email and password.
- FR-2: The system MUST allow Loan Officers, Credit Managers, and Admins to log in.
- FR-3: The system MUST send successful logins to the dashboard.
- FR-4: The system MUST reject incorrect login information.
- FR-5: The system MUST show an error message when login fails.
- FR-6: The system MUST prevent unauthenticated users from accessing protected features.

## 6. Non-Functional Requirements

- Security: Passwords should be stored securely.
- Performance: Login should respond quickly.
- Reliability: Incorrect users or passwords should not allow access.

## 7. Acceptance Criteria

- AC-1: Given a valid email and password, when the user logs in, then they are taken to the dashboard.
- AC-2: Given an incorrect email or password, when login is attempted, then access is denied and an error message appears.
- AC-3: Given any valid user role, when login succeeds, then the user can access the system.
- AC-4: Given an unauthenticated user, when they try to access a protected feature, then access is denied.

## 8. Data

User information:

- Email
- Password
- Role

## 9. API

Possible route:

- `POST /api/login`

The route checks the email and password and logs the user in if they are correct.

## 10. UI

- Email field
- Password field
- Login button
- Loading state while login is processing
- Error message for incorrect login information
- Successful login redirects the user to the dashboard

## 11. AI / ML

N/A — AI is not used for authentication.

## 12. Integration Points

- User database
- Dashboard

## 13. Dependencies

Needs:

- User database

Unblocks:

- Dashboard
- All protected features

## 14. Risks

- Risk: Unauthorized users gain access.
- Mitigation: Validate login information and require authentication before allowing access to protected features.

## 15. Rollout

1. Create login form.
2. Add login route.
3. Connect login to the user database.
4. Redirect successful users to the dashboard.

## 16. Test Plan

- AC-1: Test correct email and password redirects to the dashboard.
- AC-2: Test incorrect password and incorrect email are rejected and show an error.
- AC-3: Test successful login for Loan Officer, Credit Manager, and Admin roles.
- AC-4: Test that an unauthenticated user cannot access protected features.

## 17. Open Questions

- N/A