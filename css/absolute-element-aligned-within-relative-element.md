---
description: >-
  Sometimes we need to place an absolute element inside some relative component
  rather than the global page.
---

# Absolute element aligned within relative element

The key to this is to ensure the parent element has `"position: relative"` in it.

```text
.parentItem{
    position:realtive;
    }
.childItem{
    position:absolute;
    }
```

