# One-Click Compliance Checklist, Simplified PRD (RouteLogic)

**Author:** Me · **Status:** Draft · **Target:** High-Fidelity Prototype · **Persona:** Drivers

## 1. The Big Picture
- **Vision:** Drivers can complete a delivery and its required compliance check from one focused screen with one confirmation action.
- **Press release:** Drivers currently mark a stop delivered through three taps across three screens. In bad conditions, that friction can be enough to make them text dispatch instead of completing the workflow in the app.
One-Click Compliance Checklist brings the active stop, required checklist items, and delivery action together. Drivers review what still needs their confirmation, submit once, and get a clear result—while the checklist remains associated with the stop for manager reporting.
- **Success metric:** Increased Log Compliance Checks usage
- **Guardrail:** High Manager Satisfaction for Compliance and Reporting

## 2. The Details
### User stories
- As a driver, I want to see my active stop and required compliance checks together so that I can complete the delivery without moving between three screens.
- - Acceptance criteria: The feature core shows the active stop, required items, and delivery action on one screen.
- - The driver can identify which required items still need confirmation without opening another screen.
- As a driver, I want to confirm my completed checklist and mark the stop delivered with one action so that I spend less time interacting with the app.
- - Acceptance criteria: The primary action submits the checklist and delivery together.
- - Submission is blocked until every required item has driver confirmation.
- - The prototype shows a clear confirmation state after successful submission.
- As a driver, I want to know whether my delivery and checklist were recorded so that I do not need to contact dispatch to verify completion.
- - Acceptance criteria: The success screen identifies the stop and confirms both delivery and checklist status.
- - If submission fails, the prototype explains that completion was not recorded and offers a retry.
### Screens to build
- Entry point — Active stop
- - Active stop name and delivery address
- - Stop status
- - “Complete delivery” button
- - Short compliance-step label
- - No additional navigation required to reach the checklist
- Feature core — Delivery and checklist
- - Active stop summary
- - Required compliance items with explicit, driver-controlled checkboxes
- - Clear indication of any incomplete required item
- - Primary “Confirm checklist & mark delivered” button
- - Inline submission or retry feedback
- Success/confirmation
- - Delivery marked delivered
- - Compliance check marked complete
- - Stop identifier or name
- - Confirmation time
- - “Back to stops” button
### Functional requirements
- The active stop, required checklist items, and delivery action must appear together on the feature core screen.
- The completion action must submit delivery and checklist completion together, with one driver action.
- The completion action must remain disabled until all required items have explicit driver confirmation.
- The interface must never pre-check or auto-confirm a required compliance item on the driver’s behalf.
- After submission, the prototype must show either a confirmation that both records were saved or an error that says they were not recorded.
- On a simulated submission failure, the driver’s current checklist selections must remain visible and a retry action must be available.
- The success state must identify the stop and separately confirm delivery status and compliance-check status.
- Prototype evaluation should test whether a driver can complete the flow in 7.3 minutes or less. This is a proposed high-fidelity prototype target: half of the referenced 14.6-minute compliance step, not an agreed production commitment.
### Smart behaviors (Situation → Outcome)
- Driver opens the active stop --> Show that stop’s required checklist and delivery action together.
- One or more required items are unconfirmed --> Keep the completion action disabled and identify the outstanding items.
- Driver confirms all required items --> Enable the single “Confirm checklist & mark delivered” action.
- Driver submits successfully --> Show the success screen with both delivery and compliance completion confirmed.
- Submission fails --> Keep selections visible, state that completion was not recorded, and offer retry.
- Checklist data is missing or ambiguous --> Do not infer or invent answers; block completion and show that the required information is unavailable.
### Technical constraints
- No external APIs.
- No login or authentication flow.
- Use useState only for prototype state.
- Use local mock data for the active stop and its required checklist.
- Simulate save success and failure in the prototype; do not represent in-memory state as durable production storage.

## 3. The Logistics
### Features out
- AI-generated answers or automatic completion of compliance items.
- Broader dispatch workflow redesign.
- Coordinator dashboard or manager analytics.
- New reporting formats or audit exports.
- ETA prediction, shift handoff, or coordinator training.
- Photos, optional notes, account-specific prompts, and remembered checklist preferences.
### Edge cases & safety guard
- Incomplete checklist: Block submission and identify the unconfirmed required items.
- Missing checklist definition: Block submission and explain that required items are unavailable; do not guess.
- Submission failure: Preserve visible selections, clearly state that nothing was recorded, and offer retry.
- Repeated submission: Prevent a second submission while one is in progress; show the recorded state after success.
- Safety / hallucination guard: The prototype must not invent, infer, or preselect compliance answers. Only explicit driver confirmation counts as completion.
### Decision log
- 1. Keep delivery and compliance on one feature-core screen with one submit action. This directly addresses the driver’s three taps across three screens.
- 2. Keep compliance answers driver-confirmed and omit AI autofill. Speed must not come at the expense of accurate compliance records or the manager-satisfaction guardrail.
### Evals
- Checklist accuracy: 100%, In prototype scenarios, every required item appears for the stop, and no unconfirmed item is submitted as complete.
- Time on task: ≤7.3 minutes, Measure time from opening the active stop to seeing successful confirmation. This proposed target halves the referenced 14.6-minute compliance step.
- Unsafe completion: 0 silent completions, Across incomplete, missing-data, and failed-save scenarios, verify that the prototype never reports success or marks compliance complete without explicit confirmation and successful submission.

## MoSCoW scope
- **Must:** One-screen delivery flow; One-action completion; Accurate required items; Clear completion status; Reliable save & retry
- **Should:** Manager-visible compliance record; Prefill known stop details; Large, easy-to-tap controls; Focused exception path
- **Could:** Remember a driver’s preferred checklist choices when policy allows.; Add optional photos or notes for unusual delivery conditions.; Add configurable prompts for account-specific compliance workflows.
- **Won't (now):** AI-generated compliance answers or automatic completion of items the driver must verify.; A redesign of the broader dispatch workflow, coordinator dashboard, or manager analytics.; New reporting formats or audit exports beyond retaining the checklist with the stop.; ETA prediction, shift handoff, or coordinator training features.

---
**Builder hook:** Build a working prototype based on this PRD. Use the User Story as the core flow, Functional Requirements as build constraints, and prioritize speed and clarity over visual complexity.
