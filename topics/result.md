# Result Processing

## Sidebar

If you use the Sidebar, then the processing of the result is almost done.
You might only have to implement the [lookup](text-lookup.md) and the Embed Check Data feature.

## Embed Check Data

Note: *Only use Embed Check Data in case an [automated integration](integration-points.md) isn't feasible.*
*In all other cases we highly recommend building an automated integration.*

If enabled on the server side then the Sidebar will tell the Acrolinx Integration to Embed Check Data.
The idea of embedded check data is to enable easy integration or CMS side reporting.
Use, if you want to know:

* when the document was checked,
* which Acrolinx Score it had,
* or if it hasn't been checked at all.

Before implementing client-side reporting, check out the Acrolinx Analytics.
Acrolinx Analytics might already solve your use case.

If the integration is told to embed the check data, then it should be written back to the source document,
or CMS custom field.
Depending on your [source document format](text-extraction.md), different strategies might be used:

1. CMS document properties / custom field
2. Custom document information
3. XML processing instructions
4. Comments

The chosen strategy should depend on the document type.
Probably there are already other editors and Acrolinx Integrations dealing with the same format?
If yes, do it the same way, they do.

Make sure that:

* A new check overrides the last embedded check data, to be always up to date.
* You don't use a fixed list of keys and values. The Acrolinx Platform decides which keys should be embedded.
* In case Embed Check Data is turned off, don't touch existing embedded check data.

*Note: If you use one of the Acrolinx SDK, then you might get the Embed Check Data feature more or less for free.*
*Check the SDK API for how to implement.*
