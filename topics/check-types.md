# Check Types

Check types typically map to the different [integration points](integration-points.md).
Even if two integrations are build to implement a similar user story,
the choice of check type might differ because of different [authentication](configuration.md#Authentication) modes.

## Interactive

For integrative integrations with UI.

* Document Custom Fields: User gets prompted to fill them out, if mandatory
* Priority: High
* Analytics Document Assignment: Assign

## Automated

For automated integrations, if the authentication information for the last editing user of the content is available.

* Document Custom Fields: Optional
* Priority: Low
* Analytics Document Assignment: Assign

## Baseline

For integrations, where the user performing a check isn't the owner of the content.

* Document Custom Fields: Optional
* Priority: Low
* Analytics Document Assignment: Don't assign

## Batch

For integrations, where the user performing a check on multiple files is the owner of the content.

* Document Custom Fields: Optional
* Priority: Low
* Analytics Document Assignment: Assign
