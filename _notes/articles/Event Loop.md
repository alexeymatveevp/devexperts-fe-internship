---
---

# Event Loop
A single-threaded chain of commands which javascript browser engine executes

Every piece of JS code is executed on event loop, it should be scheduled there first and then executed synchronously. Because of synchronous execution there can be no race conditions in JS code - which is great! But on the other hand, while the single piece of code (script) is executing - nothing else happens, which means that the UI is frozen ❄

