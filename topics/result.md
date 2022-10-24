# Getting a Check Result

## Sidebar

If you use the Sidebar, then you're almost done processing the result.
You might only have to implement [lookup](text-lookup.md) and the Embed Check Data feature.

## Embed Check Data

Note: *Only use Embed Check Data if an [automated integration](checking-features.md) isn't feasible.*
*Otherwise, we highly recommend building an automated integration.*

If Embed Check Data is enabled on the Platform, then the Sidebar will tell the Acrolinx Integration to embed the check
data in a document.
The purpose of embedding check data is to ahieve an easy workflow integration or reporting in a CMS.

Use Embed Check Data if you want to know:

* when the document was checked
* the Acrolinx Score for each document
* if a document hasn't been checked at all.

Before implementing client-side reporting, check out the Acrolinx Analytics.
Acrolinx Analytics might already solve your use case.

If the integration is told to embed the check data, then it should be written back to the source document,
or CMS custom field.
Depending on your [source document format](text-extraction.md), different strategies might be used:

1. CMS document properties / custom field
2. Custom document information
3. XML processing instructions
4. Comments

Choose a strategy depending on the document type.
Probably there are already other editors and Acrolinx Integrations dealing with the same format?
If yes, do it the same way, they do.

Make sure:

* A new check overrides the last embedded check data, to be always up to date.
* You don't use a fixed list of keys and values. The Acrolinx Platform decides which keys should be embedded.
* In case Embed Check Data is turned off, don't touch existing embedded check data.

*Note: If you use one of the Acrolinx SDK, then you might get the Embed Check Data feature more or less for free.*
*Check the SDK API for how to implement.*
