
**Status:** Draft

**Version:** 1.0

**Primary Actor:** Client

**Goal:**
Allow a new client to create an account and gain access to the platform.

---

# Preconditions

- The client is not authenticated.
- The client does not have an existing account associated with the provided email address.

---

# Trigger

The client selects the **Sign Up** option.

---

# Main Success Scenario

1. The client opens the registration page.
2. The client enters the required registration information.
3. The client submits the registration form.
4. The system validates the submitted data.
5. The system verifies that the email address is not already registered.
6. The system creates a new client account.
7. The system assigns the **Client** role.
8. The system confirms successful registration.
9. The client is redirected to the sign-in page.

---

# Alternative Flows

## A1. Email already exists

At Step 5:

1. The system detects that the email address is already registered.
2. The registration process is cancelled.
3. The system displays an appropriate error message.

---

## A2. Invalid input data

At Step 4:

1. The system detects invalid or incomplete input.
2. The registration process is cancelled.
3. Validation errors are displayed.
4. The client may correct the data and submit the form again.

---

# Postconditions

## Success

- A new client account exists.
- The account is available for authentication.

## Failure

- No account is created.
- Existing data remains unchanged.

---

# Related Functional Requirements

- FR-001
- FR-004
- FR-005
- FR-008
- FR-009

---

# Related User Stories

- US-001

---

# Related Product Backlog Items

- PB-001 Authentication & Authorization

---

# Notes

The registration process for clients does not require administrator approval.

Specialist registration is described separately in **UC-002 – Register Specialist**.