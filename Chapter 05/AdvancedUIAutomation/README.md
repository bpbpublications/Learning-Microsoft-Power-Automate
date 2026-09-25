# Advanced UI Automation

This folder contains practical examples for advanced UI automation techniques in **Power Automate for desktop**, including image-based interaction and OCR scenarios.

## Examples

| Resource | Description |
|---|---|
| [Move Mouse to Image](MoveMouseToImage.md) | Use an image to locate a visual target and move the mouse pointer to it. |
| [Wait for Image](WaitForImage.md) | Wait for a visual element to appear before continuing the Desktop Flow. |
| [OCR Invoice Extraction](OCR-InvoiceExtraction.md) | Extract information from scanned invoice PDFs using OCR. |

## Recommended Learning Path

A practical sequence is:

```text
Move Mouse to Image
        ↓
Wait for Image
        ↓
OCR Invoice Extraction
```

Start with image-based interaction, then learn how to wait for a visual state, and finally apply OCR to a document-processing scenario.

## When to Use Image-Based Automation

Image-based automation can be useful when:

- A legacy application does not expose reliable UI Elements.
- A visual state is easier to identify from the screen than through selectors.
- The application uses custom or non-standard controls.

Where a stable UI Element or selector is available, prefer the more structured approach because it is generally easier to maintain.

## Related Chapter

These resources support the advanced Desktop Flow topics in **Chapter 5 – Advanced Power Automate Desktop**.

See the individual articles for the exercise steps, testing guidance, troubleshooting, and design considerations.
