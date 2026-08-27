
**Status:** Draft

**Version:** 1.0

**Primary Actor:** Administrator

**Supporting Actor:** Specialist

**Goal:**
Review a specialist registration application and decide whether to approve or reject it.

---

# Preconditions

- The administrator is authenticated.
- The administrator has the required permissions.
- A specialist application exists with the **Pending Approval** status.

---

# Trigger

The administrator opens the list of pending specialist applications.

---

# Main Success Scenario

1. The administrator opens the list of pending specialist applications.
2. The system displays all applications awaiting review.
3. The administrator selects an application.
4. The system displays the application details.
5. The administrator reviews the submitted information.
6. The administrator approves the application.
7. The system changes the specialist account status from **Pending Approval** to **Active**.
8. The system grants access to specialist functionality.
9. The system notifies the specialist that the application has been approved.

---

# Alternative Flows

## A1. Application is rejected

At Step 6:

1. The administrator rejects the application.
2. The system changes the account status to **Rejected**.
3. The system notifies the specialist that the application has been rejected.

---

## A2. Application is no longer available

At Step 3:

1. The selected application has already been processed.
2. The system informs the administrator.
3. The review process is cancelled.

---

# Postconditions

## Success

- The specialist account status is **Active**.
- The specialist can access all specialist-specific functionality.

## Failure

- The specialist account status is **Rejected**.
- The specialist cannot access specialist functionality.

---

# Related Functional Requirements

- FR-003
- FR-055
- FR-056
- FR-057

---

# Related User Stories

- US-019
- US-020

---

# Related Product Backlog Items

- PB-003 Specialist Registration
- PB-012 Administration Panel

---

# Notes

Only applications with the **Pending Approval** status may be reviewed.

Each application can be processed only once.