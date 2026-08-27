
**Status:** Draft

**Version:** 1.0

**Primary Actor:** Client / Specialist

**Supporting Actor:** System

**Goal:**
Allow a client or specialist to cancel an existing appointment while maintaining system consistency and respecting cancellation rules.

---

# Preconditions

- User is authenticated.
- User is either the client or the assigned specialist for the appointment.
- Appointment exists.
- Appointment status is **Booked** or **Confirmed**.
- Appointment has not already started.

---

# Trigger

User selects an existing appointment and chooses **Cancel Appointment**.

---

# Main Success Scenario

1. User opens their appointment list.
2. User selects an active appointment.
3. User clicks **Cancel Appointment**.
4. System checks cancellation permissions.
5. System verifies cancellation rules (e.g. time constraints).
6. System updates appointment status to **Cancelled**.
7. System frees the associated availability slot.
8. System notifies both client and specialist about cancellation.
9. System confirms successful cancellation.

---

# Alternative Flows

## A1. Appointment already started

At Step 5:

1. System detects that appointment start time has passed or is imminent.
2. Cancellation is rejected.
3. System informs user that cancellation is not allowed.

---

## A2. Unauthorized cancellation attempt

At Step 4:

1. System detects that user is neither client nor assigned specialist.
2. Operation is rejected.
3. System returns authorization error.

---

## A3. Cancellation too late (policy restriction)

At Step 5:

1. System checks cancellation policy (e.g. <24 hours before session).
2. System detects violation.
3. Cancellation is rejected or marked as requiring approval (future extension).

---

## A4. Appointment already cancelled

At Step 4–5:

1. System detects appointment status = Cancelled.
2. Operation is ignored or rejected.
3. System informs user.

---

# Postconditions

## Success

- Appointment status is **Cancelled**.
- Slot becomes available again (if applicable).
- Notifications are sent.

## Failure

- No changes are applied.
- System state remains consistent.

---

# Related Functional Requirements

- FR-030
- FR-031
- FR-034
- FR-046

---

# Related User Stories

- US-007
- US-017

---

# Related Product Backlog Items

- PB-009 Appointment Management

---

# Notes

### Cancellation Policy

Cancellation rules (e.g. time limits like 24 hours) are handled as business rules and may vary per specialist.

---

### System Consistency Rule

If an appointment is cancelled:

- it must never remain in "active" state;
- its slot must be restored if applicable;
- both participants must be notified.

---

### Future Extension

This Use Case may later support:

- cancellation fees (if payments are added)
- rescheduling flow (UC-009 extension)
- admin override cancellation