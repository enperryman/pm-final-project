# A/B Experiment Brief, RouteLogic (B2B)

## Parameters
| Parameter | Decision |
|---|---|
| Feature under test | One-Click Compliance Checklist: Collapse the 14.6-min compliance step into a smart pre-filled form |
| Persona | Driver |
| Expected outcome | The driver will no longer exit the delivery workflow application to notify dispatch the delivery status, simplifying the log compliance checks step and increasing usage and decreasing time spent. |
| Primary success metric | Time to Log Compliance Checks |
| Baseline rate | 14.6 minutes |
| Guardrail metric | Manager Satisfaction in Reporting |
| Guardrail boundary | must not drop more than 10% |
| Second guardrail | · |
| Minimum Detectable Effect | 5 |
| Sample size per arm | 1,251 |
| Traffic split | 50/50 |
| Test duration | 2 weekly cycles |
| Significance threshold | p < 0.05 (95%) |

## Control vs. Variant
- **Control (A):** Drivers are exiting the app and texting dispatch instead.
- **Variant (B):** One-Click Compliance Checklist
Entry point — Active stop --> Feature core — Delivery and checklist --> Success/confirmation
The active stop, required checklist items, and delivery action must appear together on the feature core screen.
The completion action must submit delivery and checklist completion together, with one driver action.
The completion action must remain disabled until all required items have explicit driver confirmation.
The interface must never pre-check or auto-confirm a required compliance item on the driver’s behalf.
After submission, the prototype must show either a confirmation that both records were saved or an error that says they were not recorded.
On a simulated submission failure, the driver’s current checklist selections must remain visible and a retry action must be available.
The success state must identify the stop and separately confirm delivery status and compliance-check status.
Prototype evaluation should test whether a driver can complete the flow in 7.3 minutes or less. This is a proposed high-fidelity prototype target: half of the referenced 14.6-minute compliance step, not an agreed production commitment.
- **Held constant (isolation check):** The remaining application is the same for all experiences.

## Hypothesis
> I believe that One-Click Compliance Checklist: Collapse the 14.6-min compliance step into a smart pre-filled form for Driver will result in The driver will no longer exit the delivery workflow application to notify dispatch the delivery status, simplifying the log compliance checks step and increasing usage and decreasing time spent., as measured by a 5 change in Time to Log Compliance Checks within 2 weekly cycles. We will protect Manager Satisfaction in Reporting throughout the test.

## Shipping criteria
> We will **ship** if Time to Log Compliance Checks improves by ≥ 5 at p < 0.05 (95%) and Manager Satisfaction in Reporting does not reach must not drop more than 10% after 2 weekly cycles.
> We will **iterate** if direction is positive but lift is below the MDE.
> We will **kill** if the primary metric shows no improvement or moves negatively.
> The read date is fixed at the end of 2 weekly cycles, no results reviewed before this date.
