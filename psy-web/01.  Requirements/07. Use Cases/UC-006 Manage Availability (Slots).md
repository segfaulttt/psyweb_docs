
**Status:** Draft

**Version:** 1.0

**Primary Actor:** Specialist

**Goal:**
Allow a specialist to create, manage, and remove available time slots for consultations.

---

# Preconditions

- Specialist is authenticated.
- Specialist account status is **Active**.
- Specialist has at least one active service created.

---

# Trigger

Specialist selects **Manage Availability** in dashboard.

---

# Main Success Scenario

## Create Availability Slot

1. Specialist opens availability management page.
2. Specialist selects date and time range.
3. Specialist selects associated service.
4. System validates input data.
5. System checks that no overlapping slots exist.
6. System creates a new availability slot.
7. System marks slot as **Available**.
8. System confirms successful creation.

---

## View Availability

9. System displays all existing availability slots for specialist.
10. Specialist can view slots grouped by date.

---

## Delete Availability Slot

11. Specialist selects an existing slot.
12. Specialist requests deletion.
13. System checks whether slot is not already booked.
14. System removes slot or marks it as unavailable.
15. System confirms successful deletion.

---

# Alternative Flows

## A1. Overlapping slot detected

At Step 5:

1. System detects that the new slot overlaps with an existing one.
2. Slot creation is rejected.
3. System informs specialist about conflict.

---

## A2. Slot already booked

At Step 13:

1. System detects that slot is already booked by a client.
2. Deletion is not allowed.
3. System informs specialist that cancellation requires appointment handling.

---

## A3. Invalid time range

At Step 4:

1. System detects invalid time input (end before start, past time, etc.).
2. Operation is rejected.
3. System shows validation error.

---

# Postconditions

## Success

- Availability slot is created, updated, or removed.
- System state remains consistent.
- No overlapping slots exist.

## Failure

- No changes are applied.
- Existing slots remain unchanged.

---

# Related Functional Requirements

- FR-019
- FR-020
- FR-021
- FR-022
- FR-033
- FR-034

---

# Related User Stories

- US-014

---

# Related Product Backlog Items

- PB-006 Availability Management

---

# Notes

### Important Rule

The system must guarantee that **no two availability slots for the same specialist overlap in time**.

### Booking Dependency

Availability slots are directly consumed by the booking process (UC-007).

### Concurrency Consideration

Slot creation and deletion must be handled in a way that prevents race conditions when multiple clients attempt to book or modify availability simultaneously.