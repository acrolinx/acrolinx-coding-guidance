# Check Types

Check types are usually associated with specific [checking features](checking-features.md).
Even if you build two different integrations to implement a similar use case,
each integration might use a different check type because of the different mode of [authentication](configuration.md#Authentication).

See also: [Scheduling](scheduling.md)

## Interactive

Interactive integrations with a UI (user interface).

* Custom User and Document Information Fields: If required users enter custom user or document information when
  they run checks.
* Priority: High
* Analytics Document Assignment: Assign

## Automated

Automated integrations if the authentication information for the last user who edited the content is available.

* Custom Document Information Fields: Optional
* Priority: Low
* Analytics Document Assignment: Assign

## Baseline

Integrations in which the user running a check isn't the owner of the content.

* Custom Document Information Fields: Optional
* Priority: Low
* Analytics Document Assignment: Don't assign

## Batch

Integrations in which the user running a check on several files is the owner of the content.

* Custom Document Information Fields: Optional
* Priority: Low
* Analytics Document Assignment: Assign
