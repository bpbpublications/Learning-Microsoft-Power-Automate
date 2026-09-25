# Lead Approval Business Process Flow

## Overview

This example demonstrates how to use a **Business Process Flow (BPF)** to guide users through a structured lead approval process.

A Business Process Flow provides a visual, stage-based experience that helps users follow a consistent business process and complete the required information at each stage.

## Business Scenario

Consider a sales organization that receives new leads from different sources.

Before a lead can move forward in the sales process, it must pass through a series of review and approval stages.

The Business Process Flow helps users follow these stages consistently.

## Process

The lead moves through the following stages:

```text
Lead Created
     ↓
Lead Qualification
     ↓
Lead Review
     ↓
Approval
     ↓
Qualified / Rejected
```

## Process Stages

### 1. Lead Created

The lead is created in the system and the initial information is captured.

Typical information may include:

- Lead name
- Company
- Contact information
- Lead source
- Initial requirement

The exact fields should follow the implementation used in the chapter exercise.

### 2. Lead Qualification

The lead is reviewed to determine whether it contains sufficient information for further evaluation.

Typical activities include:

- Confirming required information is available.
- Reviewing the lead source.
- Assessing the initial business requirement.
- Determining whether the lead should proceed.

### 3. Lead Review

The lead is reviewed by the appropriate business or sales team.

This stage can be used to capture additional information required for the approval decision.

Examples include:

- Business justification
- Estimated value
- Customer priority
- Additional review comments

### 4. Approval

The lead is submitted for approval according to the business process.

The approval decision may be recorded using the process and approval mechanism defined in the solution.

A conceptual flow is:

```text
Lead Review Complete
        ↓
Submit for Approval
        ↓
Approval Decision
   ┌────┴────┐
 Approved  Rejected
```

The BPF provides the stage-based guidance; the approval implementation itself should follow the design described in the chapter exercise.

### 5. Qualified / Rejected

The process reaches its final business outcome.

```text
Approved
   ↓
Qualified
```

or:

```text
Rejected
   ↓
Lead Rejected
```

Record the final outcome and any required comments according to the business process.

## Creating the Business Process Flow

A typical implementation sequence is:

1. Create the Business Process Flow.
2. Select the table or business entity used for the lead process.
3. Define the required process stages.
4. Add the appropriate data fields to each stage.
5. Configure stage transitions and business rules supported by the solution.
6. Activate the Business Process Flow.
7. Test the process with representative lead records.

The exact configuration should follow the Power Platform environment and the exercise described in the book.

## Example Stage Design

A simple stage design can be represented as:

| Stage | Purpose | Example Information |
|---|---|---|
| Lead Created | Capture initial lead | Name, company, source |
| Lead Qualification | Determine readiness | Required information, requirement |
| Lead Review | Perform business review | Value, priority, comments |
| Approval | Record decision | Approver, decision, comments |
| Qualified / Rejected | Record final outcome | Final status, reason |

## Business Rules and Validation

Each stage should make the required information clear to the user.

Before moving to the next stage, validate the fields that are important to the process.

For example:

```text
Stage Data Complete?
       ↓
   Yes → Continue
   No  → Complete Required Information
```

Avoid allowing incomplete records to progress when the missing information is necessary for a sound business decision.

## Testing

### Test 1 – Normal Approval Path

Create a lead and complete each stage in sequence.

Expected result:

```text
Lead Created
     ↓
Qualification
     ↓
Review
     ↓
Approval
     ↓
Qualified
```

### Test 2 – Rejected Lead

Create a lead that does not meet the business requirements and complete the process through the rejection outcome.

Expected result:

```text
Lead Created
     ↓
Qualification
     ↓
Review
     ↓
Approval
     ↓
Rejected
```

### Test 3 – Missing Required Information

Attempt to progress with required information incomplete.

Expected result:

The process should require the necessary information before the lead proceeds, according to the configured stage requirements.

## Common Issues

### BPF Does Not Appear

Check:

- The BPF is activated.
- The required table is included in the process.
- The user has the required permissions.
- The solution changes have been published where required.

### User Cannot Progress to the Next Stage

Check:

- Required stage fields are completed.
- Any configured business rules or conditions are satisfied.
- The user has the necessary permissions.

### Approval and BPF State Are Out of Sync

The BPF stage and the approval mechanism are related but should not be assumed to be the same thing.

Verify that the automation updates the appropriate business status and that users can clearly see the final outcome.

## Design Considerations

When designing a BPF:

- Keep the number of stages manageable.
- Group related fields within the appropriate stage.
- Make stage purpose clear to the user.
- Validate critical information before progression.
- Define clear approval and rejection outcomes.
- Keep the BPF focused on business process guidance rather than duplicating every automation detail.

## Security and Governance

Business Process Flows may expose business-sensitive information.

Review:

- Who can access the BPF.
- Who can create or update leads.
- Who can approve leads.
- Which users can move records between stages.
- Whether audit requirements apply to approval decisions.

Follow the security roles and governance model configured for the Power Platform environment.

## Related Resources

- [Chapter 3 – Building Cloud, Desktop and Business Flows](../README.md)
- [Automated Flows](../AutomatedFlows/)
- [Cloud and Desktop Integration](../CloudDesktopIntegration/)

## Notes

This example is intended to accompany the Business Process Flow section of Chapter 3 in *Learning Microsoft Power Automate*.

The current repository defines the process as **Lead Created → Lead Qualification → Lead Review → Approval → Qualified / Rejected**. The detailed stage fields, transitions, approval implementation, and business rules should follow the configuration described in the book exercise.