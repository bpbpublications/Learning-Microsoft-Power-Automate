# UI Automation Selectors

## Overview

Power Automate for desktop (PAD) uses **UI Elements** to identify and interact with applications and web pages.

UI Elements allow desktop and browser automations to interact with controls such as:

* Buttons
* Text boxes
* Links
* Menus
* Windows
* Other application controls

UI-based automation can identify controls without depending only on screen coordinates or image recognition.

This makes the automation easier to maintain when the application interface changes.

## UI Elements

UI Elements can be created in Power Automate for desktop in two common ways:

* Directly while configuring an action.
* Through the **UI Elements** pane in the Flow Designer.

The type of UI Element depends on the automation being performed.

**Desktop UI Elements** are used with UI Automation actions.

**Web UI Elements** are used with Browser Automation actions.

## Types of Selectors

Power Automate for desktop can work with different selector technologies.

### UI Automation (UIA) Selectors

UI Automation is Microsoft's modern accessibility framework for Windows applications.

UIA selectors are generally preferred for modern Windows applications.

They can provide:

* Better visibility into the application hierarchy.
* Reliable identification of controls.
* Easier maintenance when the interface changes.

UIA works well with applications based on technologies such as:

* WPF
* WinForms
* UWP

### Microsoft Active Accessibility (MSAA) Selectors

MSAA is an older accessibility technology.

It can be useful when automating legacy applications where UIA selectors are unavailable or do not identify controls reliably.

Typical examples include older:

* Win32 applications
* VB6 applications
* Legacy business applications

### UIA3 Raw Selectors

UIA3 Raw provides deeper access to the UI hierarchy.

It can be useful when standard UIA selectors cannot reliably identify an element.

Typical scenarios include:

* Electron applications
* Custom-rendered controls
* Complex application interfaces
* Applications where the standard UI tree does not expose the required element clearly

Use this option when simpler selector approaches are not sufficient.

## Capturing UI Elements

To capture a UI element in Power Automate for desktop:

1. Select **Add UI element**.
2. Move the pointer over the target application element.
3. Use **Ctrl + Left Click** to capture the element.
4. Select **Done**.

The captured element is then available in the **UI Elements** pane.

The UI Element Picker can be used with the available selector technologies, including:

```text
UIA
UIA3 Raw
MSAA
```

The appropriate technology can be selected based on the application and the reliability of the captured element.

## Desktop UI Elements and Web UI Elements

| Desktop UI Elements                                         | Web UI Elements                                     |
| ----------------------------------------------------------- | --------------------------------------------------- |
| Used with UI Automation actions                             | Used with Browser Automation actions                |
| Captured from Windows applications                          | Captured from web pages                             |
| Can use UIA, MSAA, and UIA3 Raw                             | Used for webpage content                            |
| Can automate browser controls such as tabs and address bars | Used for webpage controls such as buttons and links |

For example:

```text
Browser address bar → Desktop UI Element
Webpage button → Web UI Element
```

The browser address bar is part of the desktop browser application, whereas a button rendered inside a webpage is part of the webpage.

## UI Element Properties and Selectors

A UI Element can contain one or more selectors.

Selectors describe the path used by Power Automate for desktop to identify an element.

Selectors can be:

* Edited
* Renamed
* Disabled
* Reordered

Multiple selectors can also be configured for an important UI Element.

If one selector cannot identify the element, another configured selector may provide an alternative.

This can improve automation resilience.

## Text-Based Selectors

Text-based selectors allow an element to be identified using its displayed text.

They can be useful when the application contains predictable text values such as:

* Button labels
* Menu items
* Field names
* Status values

### Capturing an Element by Text

To capture an element based on text:

1. Open the UI Element Picker.
2. Select the target element.
3. Use the option to capture the element based on text.
4. Specify the required text value.
5. Select the appropriate matching operator.

Common operators include:

```text
Equals
Contains
```

Text-based selectors can be useful when the hierarchy of an application changes but the displayed text remains stable.

## Text Attributes

The attribute used for text-based identification depends on the automation target.

For desktop automation, the selector can use the element's **Name** attribute.

For web automation, the selector can use the element's **Text** attribute.

SAP automation is a special case where the **Text** attribute may be used instead of the typical desktop Name attribute.

## Selector Reliability

The selector strategy has a direct impact on automation reliability.

For example, a selector based on a stable button name may remain valid even when surrounding controls move.

A selector that depends heavily on a changing hierarchy can become fragile when the application interface changes.

When designing selectors, prefer attributes that are:

* Stable
* Meaningful
* Specific enough to identify the intended element
* Unlikely to change between executions

## Recommended Selector Approach

A practical approach is:

```text
Try UIA
   ↓
If unreliable → Try text-based selector
   ↓
If still unreliable → Consider MSAA
   ↓
If still unreliable → Consider UIA3 Raw
```

The best option depends on the application being automated.

## Best Practices

For reliable Power Automate Desktop automations:

* Use **UIA selectors** whenever they reliably identify the control.
* Use **MSAA** when working with legacy applications that do not expose suitable UIA information.
* Use **UIA3 Raw** for difficult or custom interfaces when standard selectors are insufficient.
* Prefer stable text-based selectors when the displayed text is predictable.
* Maintain multiple selectors for critical UI Elements when appropriate.
* Use **Desktop UI Elements** for browser controls such as the browser address bar.
* Use **Web UI Elements** for webpage content and controls.
* Avoid relying unnecessarily on screen coordinates or image recognition when a reliable UI Element is available.

## Example: Choosing a Selector

Suppose a Desktop Flow needs to click a button labelled:

```text
Submit
```

Possible approaches include:

```text
UIA selector
     ↓
Text-based selector using "Submit"
     ↓
MSAA selector
     ↓
UIA3 Raw selector
```

Start with the simplest reliable approach and move to a more advanced selector only when necessary.

## Known Limitation

When capturing an element by text and using variables with operators other than **Equal**, the visual selector editor may switch to the text editor.

This is a limitation of the visual selector builder and may require editing the selector directly.

## Practical Exercise

A useful way to understand selector behavior is to automate the same application using different selector approaches.

For example:

```text
Application
    ↓
Capture button using UIA
    ↓
Test automation
    ↓
Capture button using text
    ↓
Test automation
    ↓
Compare reliability and maintainability
```

This helps demonstrate why selector design is an important part of building robust Desktop Flows.

## Troubleshooting

### UI Element Cannot Be Captured

Check:

* The target application is open.
* Power Automate for desktop can access the application.
* The correct selector technology is being used.
* The target control is visible and accessible.

### Selector Works Once but Fails Later

Review:

* Whether the selector depends on changing text.
* Whether the application hierarchy changes.
* Whether a more stable attribute can be used.
* Whether an alternative selector should be configured.

### Legacy Application Does Not Expose a Reliable UIA Selector

Consider using:

```text
MSAA
```

or, where appropriate:

```text
UIA3 Raw
```

## Validation Checklist

* [ ] A UI Element can be captured successfully.
* [ ] The correct selector technology is selected.
* [ ] The selector identifies the intended control.
* [ ] The Desktop Flow works repeatedly.
* [ ] Critical UI Elements have a suitable fallback strategy where necessary.
* [ ] Web UI Elements and Desktop UI Elements are used for the appropriate targets.

## Related Resources

* [Chapter 3 – Building Cloud, Desktop and Business Flows](../README.md)
* [Run Application – Notepad](RunApplication-Notepad.md)
* [Invoice Entry – Legacy Application](InvoiceEntryLegacyApp.md)

## Notes

This article is intended to be used together with the Desktop Flow sections of Chapter 3 in *Learning Microsoft Power Automate*.

The current repository resource covers UIA, MSAA, UIA3 Raw, UI Elements, text-based selectors, desktop and web UI elements, selector management, best practices, and the known text-selector limitation.

Power Automate for desktop features and the user interface may change over time. Refer to the latest Microsoft documentation when the current product experience differs from the version described in the book.
