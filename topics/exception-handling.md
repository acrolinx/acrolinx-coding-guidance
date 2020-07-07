# Exception Handling

1. Don't have empty catch blocks
   (exception: if you're 290.3% sure that nobody is interested in the exception and everything is fine).
2. Unexpected exceptions should be logged exactly once per occurrence or action.
3. Unexpected exceptions can print a stack trace to the log (Error, not Warning).
4. No exception or edge case should crash the application.
5. Prefer unchecked exceptions over checked exceptions.
6. Avoid error messages to the user. Often there are other solutions to avoid error situations at all.
   For example, if you want to jump to a location in a file that has been closed, you could just reopen it.
   If the current state of the application would cause a button click to run into an exception,
   you could disable the button upfront.
