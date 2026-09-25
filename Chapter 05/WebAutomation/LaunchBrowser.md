# Launch Browser

## Overview

This example demonstrates how to launch **Microsoft Edge** and manage a browser instance in Power Automate for desktop.

Launching the browser is often the first step in a browser-based Desktop Flow.

## Scenario

A Desktop Flow needs to open a website before performing browser automation tasks.

```text
Start Desktop Flow
       ↓
Launch Microsoft Edge
       ↓
Navigate to Website
       ↓
Continue Web Automation
```

## Exercise

### Step 1 – Create a Desktop Flow

Create a Desktop Flow with a meaningful name, such as:

```text
Launch Browser Example
```

### Step 2 – Add the Launch Browser Action

Add the **Launch new Microsoft Edge** action.

Configure the action with the website required by the exercise.

For example:

```text
https://example.com
```

Use the actual website specified by the corresponding Chapter 5 exercise where applicable.

### Step 3 – Manage the Browser Instance

Store or use the browser instance returned by the launch action for subsequent browser automation steps.

Conceptually:

```text
Launch Edge
    ↓
Browser Instance
    ↓
Navigate / Interact / Extract
```

### Step 4 – Test the Flow

Run the Desktop Flow and verify that the browser opens and navigates to the expected page.

## Launch vs. Attach

A browser automation may either launch a new browser instance or work with an existing browser instance, depending on the scenario.

Use a launch action when the flow should start a new browser session.

Use an attach or existing-instance approach when the required browser session is already open and the automation needs to continue using it.

## Example

```text
Start Flow
    ↓
Launch Microsoft Edge
    ↓
Open Website
    ↓
Wait for Page
    ↓
Continue Automation
```

## Testing

### Test 1 – Browser Opens

Run the flow with a valid website address.

**Expected result:** Microsoft Edge starts and opens the specified page.

### Test 2 – Invalid Address

Use an invalid or unreachable address.

**Expected result:** The flow should handle the navigation failure according to its error-handling design.

### Test 3 – Browser Already Open

Test the scenario where an existing browser session is already present.

**Expected result:** The flow should follow the configured launch or attach strategy without unexpectedly taking control of the wrong browser instance.

## Common Issues

### Browser Does Not Open

Check:

- Microsoft Edge is installed.
- Power Automate for desktop can access the browser.
- The configured browser action is supported by the installed version.
- The target environment allows browser automation.

### Page Does Not Load

Check:

- The URL is correct.
- Network access is available.
- The site requires authentication or additional setup.
- The flow waits for the page to become ready before interacting with it.

### Wrong Browser Instance Is Used

Review how the browser instance is created, stored, and referenced by subsequent actions.

## Best Practices

- Use a clear browser-instance strategy.
- Wait for required pages or controls instead of relying only on fixed delays.
- Keep URLs configurable when the same flow runs across environments.
- Handle authentication requirements explicitly.
- Close or release browser instances when they are no longer required.
- Add an exception path for browser launch or navigation failures.

## Security Considerations

Browser sessions may contain sensitive information.

Do not store credentials, cookies, access tokens, or session data in the repository.

Use approved credential-management and authentication mechanisms for secured websites.

## Related Resources

- [Web Automation](README.md)
- [Form Filling](FormFilling.md)
- [Data Extraction](DataExtraction.md)
- [Web Scraping Pattern](WebScrapingPattern.md)

## Notes

The current repository defines this resource as launching **Microsoft Edge and managing browser instances**. The exact browser action names and options may vary by Power Automate for desktop version. fileciteturn132file0L2-L6