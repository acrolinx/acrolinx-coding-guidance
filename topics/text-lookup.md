# Text Lookup

To give writers the best possible user experience in the Sidebar, you have to implement a good lookup solution in your integration.
When a writer clicks a Sidebar card, Acrolinx uses the functions:

* `selectRanges` to highlight and focus the issue text and
* `replaceRanges` to replace the text surface corresponding to the issue text.

See [Acrolinx Sidebar API Reference](https://acrolinx.github.io/sidebar-interface/).

Not all lookup strategies work for all kinds of editors.
It's up to the developer of an integration to choose the best possible strategy.

**Note:**
The Acrolinx SDKs include ready-to-use lookup strategies.

## Terminology

### Original Text

The **Original Text** is the text that the integration sends to the Acrolinx Platform when the user clicks check in the Sidebar.
This text can also be serialized XML or HTML DOM.

### Card

A **card** in the Sidebar. A card often references one or more locations in the document.
We call these references **matches**. The card is only valid for the text at the time of the check.

### Match

A match is a part of the original text. Typically the match is related to the original text.
The match is a combination of a range and the **text surface** the [Acrolinx Platform has seen](text-extraction.md#how-acrolinx-reads-your-content).
A match could also contain a replacement for the surface.

### Surface

A **surface** is a substring of the current document or the entire text that an integration sends to the Acrolinx Platform.
The document format might be plain text or slices of XML or HTML, depending on the original text or further processing.

### Range

A **range** contains a start and an end offset. A range refers to either the **original text** or to the **current text**.

## Strategies

Contact [Acrolinx SDK support](sdk-support.md) to get access to the list of lookup strategies.
