
**Status:** Draft

**Version:** 1.0

**Primary Actor:** Client / Specialist

**Goal:**
Allow a client and a specialist to communicate via an optional messaging system before or after consultation.

---

# Preconditions

- Both users are authenticated.
- Client and specialist have an existing relationship (at least one shared appointment OR active booking context).
- Chat feature is enabled by specialist.
- Both accounts are in **Active** status.

---

# Trigger

User opens the chat section within a specialist profile or appointment page.

---

# Main Success Scenario

1. Client opens specialist profile or appointment details.
2. Client selects **Open Chat**.
3. System verifies that chat is enabled for this specialist.
4. System creates or retrieves existing chat thread between users.
5. System displays message history.
6. Client sends a message.
7. System validates message content.
8. System stores message in conversation thread.
9. System delivers message to specialist.
10. Specialist reads and responds to message.
11. System stores and delivers response to client.

---

# Alternative Flows

## A1. Chat is disabled by specialist

At Step 3:

1. System detects chat feature is disabled.
2. Chat cannot be opened.
3. System informs client that communication is not available.

---

## A2. No existing relationship

At Step 2–3:

1. System detects no valid relationship (no appointment or permission).
2. Chat access is denied.
3. System returns authorization error.

---

## A3. Invalid message content

At Step 7:

1. System detects empty or invalid message.
2. Message is not sent.
3. System prompts user to correct input.

---

## A4. Specialist does not respond

At Step 10:

1. Message remains stored in chat history.
2. System does not require immediate response.
3. Conversation remains open.

---

# Postconditions

## Success

- Messages are stored in system.
- Both participants can view conversation history.
- Communication channel is established.

## Failure

- No message is stored (if validation fails or access denied).

---

# Related Functional Requirements

- FR-037
- FR-038
- FR-039

---

# Related User Stories

- US-010

---

# Related Product Backlog Items

- PB-011 Chat

---

# Notes

### Important Constraint

Chat is **optional feature per specialist**, meaning:

- some specialists may disable it completely;
- chat is not required for booking or completing consultations.

---

### Simplification (MVP)

For MVP, chat is defined as:

- simple message exchange
- no delivery status (sent/delivered/read)
- no file sharing
- no typing indicators

---

### Future Extensions

This Use Case can later evolve into:

- WebSocket real-time messaging
- message status tracking
- file attachments
- notifications integration
- AI-assisted chat summaries