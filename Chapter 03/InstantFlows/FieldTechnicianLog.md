# Field Technician Log

## Overview

This example demonstrates how to build an **Instant Cloud Flow** that allows a field technician to manually record equipment information.

The technician provides the equipment ID, current status, and notes. The flow then stores the information for tracking and follow-up.

## Business Scenario

Field technicians often need to record the status of equipment while working at a customer site or in the field.

Instead of maintaining a separate manual process, the technician can start an **Instant Cloud Flow** from Power Automate, enter the required information, and submit the log.

The flow follows this sequence:

Technician starts the flow
        ↓
Enter Equipment ID
        ↓
Select Equipment Status
        ↓
Enter Notes
        ↓
Store Technician Log

## Capture Technician Information

The flow uses a manual trigger and captures three pieces of information:

| Input | Purpose |
|---|---|
| Equipment ID | Identifies the equipment being inspected or serviced |
| Status | Records the current equipment status |
| Notes | Captures additional information from the technician |

### Equipment ID

The technician enters the identifier of the equipment.

Example:

`EQ-1001`

### Status

The technician provides the current equipment status.

Example values:

- Operational
- Needs Maintenance
- Out of Service

### Notes

The technician can provide additional information about the equipment.

Example:

`Unusual noise detected during inspection.`

## Build the Instant Cloud Flow

1. Open the appropriate Power Automate environment.
2. Create a new **Instant cloud flow**.
3. Select the manual trigger.
4. Add an input for **Equipment ID**.
5. Add an input for **Status**.
6. Add an input for **Notes**.
7. Add the action required to store the technician log.
8. Map each input to the corresponding destination field.
9. Save the flow.
10. Test the flow using sample information.

> **Note:** The exact destination and connector should follow the implementation described in the corresponding chapter exercise.

## Example

A technician might submit:

Equipment ID: `EQ-1001`

Status: `Needs Maintenance`

Notes: `Unusual noise detected during inspection.`

The flow captures these values and creates a technician log.

## Testing

### Test 1 – Operational Equipment

**Input**

- Equipment ID: `EQ-1001`
- Status: `Operational`
- Notes: `Equipment operating normally.`

**Expected result:** A technician log is created successfully.

### Test 2 – Equipment Requiring Maintenance

**Input**

- Equipment ID: `EQ-1002`
- Status: `Needs Maintenance`
- Notes: `Unusual noise detected.`

**Expected result:** A technician log is created with the maintenance status and notes.

### Test 3 – Multiple Equipment Entries

Run the flow multiple times using different equipment IDs.

**Expected result:** Each flow run creates a separate technician log entry.

## Expected Result

After completing the exercise, the field technician should be able to:

1. Start the Instant Cloud Flow.
2. Enter the equipment ID.
3. Provide the equipment status.
4. Add notes.
5. Submit the information.
6. Store the resulting technician log.

The flow provides a simple and consistent way to record equipment information.

## Validation Checklist

- [ ] The flow can be started manually.
- [ ] Equipment ID can be entered.
- [ ] Status can be provided.
- [ ] Notes can be entered.
- [ ] The information is stored correctly.
- [ ] Multiple executions create separate records.
- [ ] The flow run completes successfully.

## Common Issues

### Flow Does Not Start

Check:

- The flow is turned on.
- The user has permission to run the flow.
- The correct Power Automate environment is selected.

### Input Is Not Available

Check that the corresponding manual-trigger input was added to the flow.

### Technician Log Is Not Created

Check:

- The destination connection.
- Required destination fields.
- User permissions.
- Mapping between flow inputs and destination fields.

### Incorrect Data Is Stored

Review the dynamic content used in the destination action and verify that each input is mapped to the correct field.

## Security and Data Considerations

Equipment information may be associated with customers, sites, or employees.

Review:

- Who can run the flow.
- Who can view technician logs.
- Permissions on the destination system.
- Data retention requirements.

Do not store passwords, API keys, connection secrets, or other sensitive information in this repository.

## Related Resources

- [Chapter 3 – Building Cloud, Desktop and Business Flows](../README.md)
- [Sample Data](../SampleData/)
- [Expressions](../Expressions/)

## Notes

This example is intended to be used together with the corresponding section of Chapter 3 in *Learning Microsoft Power Automate*.

The current repository defines this example as a manual trigger that captures **Equipment ID, Status, and Notes**.

The exact destination used to store the technician log should follow the implementation described in the book.
