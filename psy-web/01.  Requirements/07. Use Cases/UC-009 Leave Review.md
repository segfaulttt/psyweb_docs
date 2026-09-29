**Status:** Draft

**Version:** 2.0

**Primary Actor:** Client

**Supporting Actor:** System

**Goal:**

Allow a Client to leave feedback for a Specialist after at least one consultation between them has been conclusively resolved as having occurred.

---

# Preconditions

- Client is authenticated.
- Specialist exists.
- At least one historical Booking exists between the Client and Specialist with a SessionOutcome satisfying:

```text
resolutionStatus = RESOLVED
finalOutcome = OCCURRED
```

- Review for this Client-Specialist pair does not already exist.

---

# Trigger

Client chooses to leave a Review for a Specialist.

---

# Main Success Scenario

1. Client opens the Specialist or Review interface.
2. Client selects **Leave Review**.
3. System identifies the authenticated Client and target Specialist.
4. System checks whether a Review already exists for the Client-Specialist pair.
5. System checks historical Booking and SessionOutcome data for the same Client and Specialist.
6. System verifies that at least one SessionOutcome is `RESOLVED / OCCURRED`.
7. Client enters a rating and optional comment.
8. Client submits the Review.
9. System validates the Review data.
10. System stores one Review linked to the Client and Specialist.
11. System confirms successful submission.

---

# Alternative Flows

## A1. No Eligible SessionOutcome

At Step 6:

1. System finds no `RESOLVED / OCCURRED` SessionOutcome for the Client-Specialist pair.
2. Review creation is rejected.
3. System informs the Client that Review creation is not yet allowed.

The following do not satisfy eligibility:

```text
PENDING
DISPUTED
UNVERIFIED
RESOLVED / DID_NOT_OCCUR
```

---

## A2. Review Already Exists

At Step 4:

1. System detects an existing Review for the same Client and Specialist.
2. Creation of another Review is rejected.
3. Client may edit the existing Review instead.

---

## A3. Invalid Review Data

At Step 9:

1. System detects invalid Review data.
2. Review is not saved.
3. System returns validation errors.

---

# Postconditions

## Success

- Review is stored in the system.
- Review is linked to the Client and Specialist.
- No Booking identifier is stored as Review ownership.
- Specialist rating queries can include the new Review.

## Failure

- No new Review is created.
- Existing system state remains unchanged.

---

# Related Functional Requirements

- FR-047
- FR-048
- FR-049
- FR-050

---

# Related User Stories

- US-009

---

# Related Product Backlog Items

- PB-010 Reviews

---

# Notes

## Critical Rule

Review eligibility exists when at least one consultation for the same Client and Specialist has:

```text
SessionOutcome.resolutionStatus = RESOLVED
SessionOutcome.finalOutcome = OCCURRED
```

The final OCCURRED outcome may result from:

- two compatible OCCURRED reports;
- one OCCURRED report finalized after reporting timeout;
- administrative resolution of a dispute to OCCURRED.

Dual confirmation is not required as a separate Review condition.

---

## Relationship Rule

The Review belongs to:

```text
Client + Specialist
```

not to an individual appointment.

At most one Review may exist for the same pair.

The existing Review may be edited later.

---

## Rating

For the MVP, Specialist rating is calculated from Review data when queried.

A persisted `rating_avg` field is not required.

---

## Future Extension

This Use Case may later include:

- additional moderation workflows;
- fraud-prevention mechanisms;
- rating caching or projection for performance;
- more advanced reputation models.