# Wait for Image

## Overview

This example demonstrates how to use the **Wait for Image** action in Power Automate for desktop when an automation needs to wait for a visual element to appear before continuing.

This is useful in applications where the required control cannot be identified reliably through standard UI Elements or selectors.

## Scenario

Consider a legacy application that takes an unpredictable amount of time to display a confirmation button after an operation.

Instead of using a fixed delay, the Desktop Flow can wait for the expected image to appear.

```text
Start Desktop Flow
       ↓
Perform Action
       ↓
Wait for Target Image
       ↓
Image Found
       ↓
Continue Automation
```

## Exercise

### Step 1 – Prepare the Target Application

Open the application containing the visual element that the flow needs to wait for.

Make sure the target state can be identified visually.

### Step 2 – Capture the Target Image

Capture a clear image of the expected visual element.

Choose an image that is distinctive enough to identify the target reliably.

### Step 3 – Add the Wait for Image Action

Add the **Wait for Image** action to the Desktop Flow.

Configure the target image and the appropriate wait or timeout settings supported by the Power Automate for desktop version used in the exercise.

### Step 4 – Continue After the Image Appears

Add the next action after the image-detection step.

The logical flow is:

```text
Perform Previous Action
        ↓
Wait for Image
        ↓
Target Appears
        ↓
Next Action
```

## Why Use Wait for Image?

A fixed delay assumes that an application will always respond within the same amount of time.

A visual wait is based on the actual state of the application.

For example:

```text
Fixed Delay
    ↓
Wait 10 seconds
    ↓
Continue
```

versus:

```text
Wait for Image
    ↓
Continue when target appears
```

The second approach can be more suitable when application response time varies.

## Example

Suppose a legacy application displays a **Processing Complete** image after a transaction finishes.

The Desktop Flow can wait for that image before moving to the next step:

```text
Submit Transaction
       ↓
Wait for Processing Complete Image
       ↓
Continue
       ↓
Record Result
```

## Testing

### Test 1 – Image Appears Quickly

Run the flow when the target image appears soon after the previous action.

Expected result:

The flow detects the image and continues.

### Test 2 – Image Appears Slowly

Run the flow when the application takes longer to display the target.

Expected result:

The flow waits for the configured condition instead of immediately continuing.

### Test 3 – Image Never Appears

Run the flow when the target image does not appear.

Expected result:

The configured timeout or failure behavior is reached and the flow handles the condition appropriately.

## Best Practices

- Use a distinctive target image.
- Capture only the visual area required to identify the state.
- Configure a reasonable timeout.
- Avoid very small or unstable visual regions.
- Prefer UI Elements or selectors when they provide a reliable alternative.
- Add an exception path for cases where the image does not appear.

## Common Issues

### Image Is Not Detected

Check:

- The target application is visible.
- The image matches the current screen appearance.
- Display scaling and resolution are consistent.
- The target is not hidden behind another window.

### Image Is Detected Inconsistently

Check whether:

- The application changes the image appearance dynamically.
- The captured image contains unnecessary surrounding content.
- Windows scaling or display settings differ between machines.
- The target is partially obscured.

### Flow Waits Too Long

Review the timeout configuration and make sure the expected image can actually appear under the test conditions.

## Design Considerations

Image-based waits are useful for applications with limited automation interfaces, but they depend on the visual state of the screen.

Use them when appropriate and prefer more stable automation methods when the application exposes reliable UI Elements or selectors.

## Security and Data Considerations

Captured images may contain customer, employee, financial, or other sensitive information.

Do not store screenshots containing confidential information in the repository.

Do not store passwords, API keys, credentials, or other secrets in this repository.

## Related Resources

- [Chapter 5 – Advanced Power Automate Desktop](../README.md)
- [Move Mouse to Image](MoveMouseToImage.md)
- [OCR Invoice Extraction](OCR-InvoiceExtraction.md)

## Notes

This example is intended to accompany the advanced UI automation section of Chapter 5 in *Learning Microsoft Power Automate*.

The current repository defines this resource as **Wait for Image action configuration and best practices**.