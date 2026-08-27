
**Status:** Draft

**Version:** 1.0

**Primary Actor:** Specialist

**Goal:**
Allow a specialist to create a consultation service that clients can book.

---

# Preconditions

- Specialist is authenticated.
- Specialist account status is **Active**.
- Specialist profile is published (or allowed to have services created even if hidden — TBD, currently allowed).

---

# Trigger

Specialist selects **Create Service** action in dashboard.

---

# Main Success Scenario

1. Specialist opens service creation form.
2. Specialist enters service details.
3. Specialist submits the form.
4. System validates input data.
5. System verifies specialist permissions.
6. System creates a new service linked to the specialist.
7. System saves service with **Active** status.
8. System confirms successful creation.
9. Service becomes visible in specialist profile.

---

# Alternative Flows

## A1. Invalid input data

At Step 4:

1. System detects missing or invalid fields.
2. Service is not created.
3. System displays validation errors.
4. Specialist corrects input and retries.

---

## A2. Specialist is not active

At Step 5:

1. System detects that specialist status is not **Active**.
2. Service creation is denied.
3. System informs specialist that account is not active.

---

## A3. Specialist tries to create service without permissions

At Step 5:

1. System detects insufficient permissions.
2. Operation is rejected.
3. System returns authorization error.

---

# Postconditions

## Success

- New service exists in system.
- Service is linked to specialist.
- Service is available for viewing and booking.

## Failure

- No service is created.
- System state remains unchanged.

---

# Related Functional Requirements

- FR-015
- FR-016
- FR-017
- FR-018
- FR-030

---

# Related User Stories

- US-013

---

# Related Product Backlog Items

- PB-005 Consultation Services

---

# Notes

A service represents a type of consultation offered by a specialist.

A service is required before availability slots can be created.