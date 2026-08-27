
**Status:** Draft

**Version:** 1.0

**Primary Actor:** User (Client / Specialist / Administrator)

**Goal:**
Allow registered users to authenticate and access the platform according to their role and status.

---

# Preconditions

- User account exists.
- User account is not in **Rejected** state.
- User account is not blocked (Suspended).
- User has valid credentials.

---

# Trigger

User selects the **Login / Sign In** option.

---

# Main Success Scenario

1. User opens the login page.
2. User enters email and password.
3. User submits login form.
4. System validates input data.
5. System checks credentials against stored user data.
6. System verifies user account status is **Active**.
7. System creates authenticated session (or issues JWT token).
8. System redirects user to the platform dashboard.
9. System loads role-based interface (Client / Specialist / Administrator).

---

# Alternative Flows

## A1. Invalid credentials

At Step 5:

1. System cannot match email/password.
2. Authentication is rejected.
3. System shows error message: invalid credentials.
4. User may retry login.

---

## A2. Account not active

At Step 6:

1. System detects account is not **Active**.
2. Authentication is denied.
3. System informs user that account is pending approval or blocked.

---

## A3. Account rejected

At Step 6:

1. System detects account status = **Rejected**.
2. Authentication is denied.
3. System informs user that account was rejected.

---

## A4. Account suspended

At Step 6:

1. System detects account status = **Suspended**.
2. Authentication is denied.
3. System informs user that account is temporarily blocked.

---

# Postconditions

## Success

- User is authenticated.
- Session or token is created.
- User gains access based on role.

## Failure

- No session is created.
- User remains unauthenticated.

---

# Related Functional Requirements

- FR-005
- FR-006
- FR-007
- FR-008
- FR-009

---

# Related User Stories

- US-001
- US-011

---

# Related Product Backlog Items

- PB-001 Authentication & Authorization

---

# Notes

Authentication mechanism (JWT, session-based auth, etc.) is not defined at this level and will be specified in architecture documentation.

Login is role-agnostic: system determines access rights after authentication.