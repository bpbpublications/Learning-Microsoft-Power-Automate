# Move Mouse to Image

## Overview

This example demonstrates how to use the **Move mouse to image** action in Power Automate for desktop.

The action can locate a visual element on the screen and move the mouse pointer to the detected image location.

This approach is useful when a reliable UI Element or selector is not available.

## Scenario

Consider a legacy or image-based application where a control cannot be identified reliably through standard UI automation.

A Desktop Flow can use an image of the target control to locate it on the screen.

```text
Start Desktop Flow
       ↓
Display Target Application
       ↓
Locate Target Image
       ↓
Move Mouse to Image
       ↓
Continue Automation
```

## Exercise

### Step 1 – Prepare the Target Application

Open the application that contains the visual element you want to locate.

Make sure the target element is visible on the screen.

### Step 2 – Capture the Image

Capture or provide a suitable image of the target control.

The image should contain enough visual detail to distinguish the target from nearby elements.

### Step 3 – Add the Action

Add the **Move mouse to image** action to the Desktop Flow.

Configure it with the target image according to the Power Automate for desktop version used in the exercise.

### Step 4 – Run the Flow

Run the Desktop Flow and verify that the mouse pointer moves to the location of the target image.

## Example

Suppose an application contains a visually distinctive button that cannot be captured reliably as a UI Element.

The flow can locate the button using an image:

```text
Application
    ↓
Find Button Image
    ↓
Move Mouse to Button
    ↓
Continue with Next Action
```

## Testing

### Test 1 – Clear Target

Use a clear and unique image of the target control.

Expected result:

The mouse pointer moves to the detected location.

### Test 2 – Target Changes Position

Move the target control to another location while keeping its appearance similar.

Expected result:

The image-based action can locate the target based on its visual appearance rather than a fixed coordinate, subject to the image-matching capabilities of the action.

### Test 3 – Target Not Visible

Run the flow when the target image is not visible.

Expected result:

The action should follow its configured behavior for an image that cannot be found. The flow should handle the resulting condition appropriately.

## Best Practices

- Use clear and distinctive target images.
- Avoid capturing unnecessary surrounding content.
- Keep the application at a consistent visual state where possible.
- Avoid relying on image automation when a stable UI Element is available.
- Test image matching at the display resolution and scaling used by the target machine.
- Provide an appropriate fallback or exception path when the image cannot be found.

## Common Issues

### Image Cannot Be Found

Check:

- The target application is visible.
- The target image matches the current screen appearance.
- The display scaling and resolution have not changed unexpectedly.
- The target is not hidden behind another window.

### Image Matching Is Unreliable

Check whether:

- The target image contains too much surrounding content.
- The target changes appearance dynamically.
- Windows display scaling differs between environments.
- The application theme or state changes the target appearance.

### The Mouse Moves to the Wrong Location

Use a more distinctive image and reduce unnecessary content around the target.

## Design Considerations

Image-based automation is generally more sensitive to visual changes than selector-based automation.

Use it when the application's UI does not expose a reliable automation interface, and prefer UI Elements or selectors when those provide a stable alternative.

## Security and Data Considerations

Screenshots and captured images may contain sensitive information.

Avoid storing screenshots that contain customer, employee, credential, or confidential business information in the repository.

Do not store passwords, API keys, credentials, or other secrets in this repository.

## Related Resources

- [Chapter 5 – Advanced Power Automate Desktop](../README.md)
- [Wait for Image](WaitForImage.md)
- [OCR Invoice Extraction](OCR-InvoiceExtraction.md)

## Notes

This example is intended to accompany the advanced UI automation section of Chapter 5 in *Learning Microsoft Power Automate*.

The current repository defines this resource as examples for the **Move Mouse to Image** action.