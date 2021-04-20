---
description: >-
  Code to debounce an handle simultaneous event that only need a controlled
  aaction.
---

# Debouncing a an event

In some cases, we need to capture certain events that happen continuously, such as a mouse scroll, or click, so that the action that we need to do is only run once in a controlled manner. To do this, we can use  this debounce function .  I have set a timer of 500 ms for this function.

```text
var debounce_timer;

window.addEventListener("wheel", function (val) {

    if (debounce_timer) {
        window.clearTimeout(debounce_timer);
    }
    debounce_timer = window.setTimeout(function () {

     yourFunction(val);
    }, 500);
});

```

