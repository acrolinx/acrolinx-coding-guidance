# Text lookup

To give writers the best possible Sidebar user experience, implement a good lookup solution in your integration.
When a writer clicks a Sidebar card, Acrolinx uses the functions:

* `selectRanges` to highlight and focus on the issue text.
* `replaceRanges` to replace the text surface corresponding to the issue text.

See [Acrolinx Sidebar API reference](https://acrolinx.github.io/sidebar-interface/).

Not all lookup strategies work for all kinds of editors.
The developer of an integration is responsible for choosing the best possible strategy.

**Note:**
The Acrolinx SDKs include working lookup strategies.

## Terminology

### Original text

The **original text** is the text that an integration sends to Acrolinx when the user clicks CHECK in the Sidebar.
This text can also be serialized XML or an HTML DOM.

### Card

A Sidebar **card** often references one or more locations in the document.
We call these references **matches**. A card is only valid for the text at the time of the check.

### Match

A match is a part of the original text. The match is a combination of a range and the **text surface** that 
[Acrolinx has seen](text-extraction.md#how-acrolinx-reads-your-content).
A match can also contain a replacement for the surface.

### Surface

A **surface** is a substring of the current document or the entire text that an integration sends to Acrolinx.
The document format could be plain text or pieces of XML or HTML, depending on the original text or additional processing.

### Range

A **range** contains a start and an end offset. A range refers to either the **original text** or to the **current text**.

## Strategies

Contact [Acrolinx Support](support.md) for a list of lookup strategies.
