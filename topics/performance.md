# Performance

During development, the focus should be on readability, not on locally optimized performance.
It's easier to optimize readable code than to make code with good performance readable.
If the code is unreadable and not performant, what do you do?

* Nevertheless, user actions should complete within 200 ms. If they're slower, try to optimize your code.
  If you can't get under that threshold, display some kind of progress status. The application must not hang at any point.
* Don't perform long-running operations on the main thread blocking the user interface.
* The code shouldn't have extensive memory consumption.