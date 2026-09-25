# Offline and Intermittent Connectivity Resilience

## Overview

Automations that operate across locations or unreliable networks need to account for temporary connectivity loss.

## Resilience Pattern

```text
Attempt Operation
      ↓
Connectivity Available?
   ┌──┴──┐
  Yes   No
   ↓     ↓
Process Queue / Retry
       ↓
   Reconnect
       ↓
 Resume Processing
```

## Design Considerations

- Retry only operations that are safe to repeat.
- Persist work that must not be lost.
- Avoid duplicate processing.
- Define maximum retry duration.
- Record failures for later investigation.

## Related Resources

- [Edge and Distributed Automation](README.md)
- [Scalability](../Hyperautomation/README.md)
