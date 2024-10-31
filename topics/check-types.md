# Check types

Check types are usually associated with specific [checking features](checking-features.md).
If you build two different integrations to implement a similar use case,
each integration might use a different check type because of the different methods of [authentication](configuration.md#Authentication).

See also: [Scheduling](scheduling.md)

## Interactive

Interactive integrations with a user interface (UI).

* Custom user and document information fields: If enabled, users enter custom user or document information when
  they run checks.
* Priority: high
* Analytics document assignment: assign

## Automated

Automated integrations in which the authentication information of the last user who edited the content is available.

* Custom document information fields: optional
* Priority: low
* Analytics document assignment: assign

## Baseline

Integrations in which the user who checks does not own the content.

* Custom document information fields: optional
* Priority: Low
* Analytics document assignment: don't assign

## Batch

Integrations in which the user who checks several files owns the content.

* Custom document information fields: optional
* Priority: low
* Analytics document assignment: assign
