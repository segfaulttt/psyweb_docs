
**Status:** Draft

**Version:** 1.0

**Primary Actor:** Client

**Supporting Actor:** Specialist, System

**Goal:**
Allow a client to leave a review for a completed appointment, ensuring reviews are only created after successful consultation.

---

# Preconditions

- Client is authenticated.
- Appointment exists.
- Appointment status is **Completed**.
- Appointment is linked to the client.
- Review for this appointment does not already exist.

---

# Trigger

Client selects a completed appointment and chooses **Leave Review**.

---

# Main Success Scenario

1. Client opens appointment history.
2. Client selects a completed appointment.
3. Client selects **Leave Review** option.
4. System verifies appointment status is **Completed**.
5. System checks that no review already exists.
6. Client enters rating and optional comment.
7. Client submits review.
8. System validates input data.
9. System stores review linked to appointment, client, and specialist.
10. System marks review as **Published**.
11. System updates specialist rating (if applicable).
12. System confirms successful submission.

---

# Alternative Flows

## A1. Appointment not completed

At Step 4:

1. System detects appointment is not marked as **Completed**.
2. Review creation is rejected.
3. System informs client that review is not allowed yet.

---

## A2. Review already exists

At Step 5:

1. System detects existing review for appointment.
2. Operation is rejected.
3. System prevents duplicate review.

---

## A3. Invalid review data

At Step 8:

1. System detects invalid rating or empty required fields.
2. Review is not saved.
3. System displays validation errors.

---

# Postconditions

## Success

- Review is stored in system.
- Review is linked to appointment and specialist.
- Specialist rating is updated.

## Failure

- No review is created.
- System state remains unchanged.

---

# Related Functional Requirements

- FR-033
- FR-034
- FR-035
- FR-036

---

# Related User Stories

- US-009

---

# Related Product Backlog Items

- PB-010 Reviews

---

# Notes

### Critical Rule

A review can only be created if:

- appointment is completed;
- appointment belongs to the client;
- no previous review exists for that appointment.

---

### System Behavior

Reviews are immediately visible after creation unless moderation is added later.

---

### Future Extension

This Use Case may later include:

- admin moderation before publishing
- edit/delete review rules
- fraud prevention (fake reviews)
- weighted rating system