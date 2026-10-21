# F9 — User Management

## Metadata

- Feature ID: F9
- Severity: High
- Status: Missing
- Effort: Small
- Depends on: User Authentication

## 1. Problem

Admins need a way to manage the users who have access to the loan application system.

## 2. Goals

- Allow Admins to manage users.
- Allow Admins to assign roles and authority.
- Allow Admins to delete users.

## 3. Non-Goals

- Loan Officers managing users.
- Credit Managers managing users.
- Users changing their own roles or authority.

## 4. User Story

As an Admin, I want to manage users so that I can control who has access to the system and what they are allowed to do.

## 5. Functional Requirements

- FR-1: The system MUST only allow Admins to manage users.
- FR-2: Admins MUST be able to create users.
- FR-3: Admins MUST be able to update users.
- FR-4: Admins MUST be able to delete users.
- FR-5: Admins MUST be able to assign roles.
- FR-6: Admins MUST be able to assign user authority.

## 6. Non-Functional Requirements

- Security: Only Admins can access user management.
- Reliability: User changes must save correctly.
- Performance: User information should load quickly.

## 7. Acceptance Criteria

- AC-1: Given an Admin, when they open User Management, then they can view users.
- AC-2: Given an Admin, when they create or update a user, then the information is saved.
- AC-3: Given an Admin, when they assign a role or authority, then the user's permissions are updated.
- AC-4: Given an Admin, when they delete a user, then the user is removed.
- AC-5: Given a non-Admin, when they try to access User Management, then access is denied.
- AC-6: Given a user management action fails, when the Admin attempts the change, then an error message is shown.

## 8. Data

User information includes:

- First name
- Last name
- Email
- Role
- Authority

Roles include:

- Loan Officer
- Credit Manager
- Admin

## 9. API

Possible routes:

- `GET /api/users`
- `POST /api/users`
- `PUT /api/users/:id`
- `DELETE /api/users/:id`

These routes allow Admins to view, create, update, and delete users.

## 10. UI

- User Management screen
- List of users
- Create User button
- Edit User option
- Delete User option
- Role selection
- Authority selection
- Loading state while users are being retrieved
- Error message if a user management action fails

## 11. AI / ML

N/A — AI is not used for user management.

## 12. Integration Points

- Authentication
- User roles
- User database

## 13. Dependencies

Needs:

- User Authentication
- Admin role

Unblocks:

- Managing access to the system

## 14. Risks

- Risk: A non-Admin changes user permissions.
- Mitigation: Restrict all user management actions to Admins.

## 15. Rollout

1. Create User Management screen.
2. Add create and edit user functions.
3. Add role and authority controls.
4. Add delete function.
5. Test Admin permissions.

## 16. Test Plan

- AC-1: Test that Admins can view users.
- AC-2: Test creating and editing a user.
- AC-3: Test assigning roles and changing authority.
- AC-4: Test deleting a user.
- AC-5: Test that non-Admins cannot access User Management.
- AC-6: Test that a failed user management action shows an error message.

## 17. Open Questions

- N/A