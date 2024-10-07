# Performance

During development, your focus should be on readability, not on locally optimized performance.
It's easier to optimize readable code than to make code with good performance readable.
If your code is unreadable and not performant, what do you do?

* Nevertheless, user actions should complete within 200 ms. If they're slower, try to optimize your code.
  If you can't stay below that threshold, show some kind of progress status. You application must not hang at any point.
* Don't perform long-running operations on the main thread that block the user interface.
* Your code shouldn't have extensive memory consumption.

See also: [Scheduling](scheduling.md)
