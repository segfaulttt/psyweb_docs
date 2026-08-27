
**Status:** Draft

**Version:** 1.0

**Primary Actor:** Client

**Supporting Actor:** Specialist

**Goal:**
Allow a client to book an available consultation slot with a specialist.

---

# Preconditions

- Client is authenticated.
- Client account status is **Active**.
- Specialist account status is **Active**.
- Specialist has at least one active service.
- Specialist has available slots.
- Selected slot is not already booked.

---

# Trigger

Client selects a service and chooses an available time slot.

---

# Main Success Scenario

1. Client opens specialist profile.
2. Client selects a consultation service.
3. System displays available slots for selected service.
4. Client selects an available slot.
5. System validates slot availability.
6. System verifies no time conflict with client's existing appointments.
7. System verifies specialist is still available at that time.
8. System creates a new appointment.
9. System marks selected slot as **Booked**.
10. System links appointment to client and specialist.
11. System confirms successful booking.
12. System sends notifications to both client and specialist.

---

# Alternative Flows

## A1. Slot already booked

At Step 5:

1. System detects that slot is no longer available.
2. Booking is rejected.
3. System informs client to choose another slot.

---

## A2. Client has conflicting appointment

At Step 6:

1. System detects overlapping appointment for client.
2. Booking is rejected.
3. System informs client about time conflict.

---

## A3. Specialist became unavailable

At Step 7:

1. System detects that specialist has removed or modified availability.
2. Booking is rejected.
3. System prompts client to refresh available slots.

---

## A4. Slot removed during booking process

At Step 5 or 7:

1. System detects that slot was deleted by specialist.
2. Booking is cancelled.
3. System informs client.

---

# Postconditions

## Success

- Appointment is created in system.
- Slot is marked as booked.
- Client and specialist are linked to appointment.
- Notifications are sent.

## Failure

- No appointment is created.
- Slot remains unchanged (or already removed).
- System state remains consistent.

---

# Related Functional Requirements

- FR-027
- FR-028
- FR-029
- FR-030
- FR-031
- FR-034
- FR-046

---

# Related User Stories

- US-006
- US-007
- US-008

---

# Related Product Backlog Items

- PB-008 Appointment Booking
- PB-009 Appointment Management

---

# Notes

### Critical Rule — No Double Booking

The system must guarantee that:

- a slot cannot be booked twice;
- a client cannot have overlapping appointments;
- a specialist cannot be double-booked.

---

### Concurrency Requirement

Booking must be **atomic operation**.

If two clients attempt to book the same slot simultaneously, only one request must succeed.

This will later require:

- transaction management
- locking strategy (optimistic or pessimistic locking)
- database constraints

---

### Domain Dependency Chain

Booking depends on:

```
Specialist → Service → Availability Slot → Appointment
```

---

### Future Extension

This use case will later support:

- cancellation policies
- refunds (if payments are added)
- rescheduling logic