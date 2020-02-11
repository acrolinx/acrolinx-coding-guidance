# Text Lookup

To make use of all features of the Acrolinx Sidebar, an integration must implement a good solution for lookup.
The lookup is used in the functions `selectRanges` and `replaceRanges` (See [Acrolinx Sidebar API Reference](https://acrolinx.github.io/sidebar-interface/)).
The Sidebar will use these to highlight, focus, and replace the text surface related to the card the users clicks on.

Not all lookup strategies will function for all kinds of editors.
It's up to the developer of an integration to select the best fitting strategy.

**Note:**
If you use one of the Acrolinx SDKs, different lookup strategies are already implemented and ready to use.

## Terminology

### Original Text

The **Original Text** is the text that was sent to the Acrolinx Platform, after the user clicked on check in the Sidebar.
This text could also be a serialized XML or HTML DOM.

### Card

A **card** in the Sidebar. The card typically references to one or more places in the document.
These references are called **matches**. The card as such is only valid for the text at check time.

### Match

A match is a part of the original text. Typically the match is related to the original text.
The match is a combination of a range as well as the **text surface** the [Acrolinx Platform has seen](text-extraction.md#how-acrolinx-reads-your-content).
A match could also contain a replacement for the surface.

### Surface

A **surface** is a substring of the entire text that was sent to the Acrolinx Platform or of the current document.
This could be plain text as well as slices of XML or HTML depending on the original text or further processing.

### Range

A **range** contains a start and an end offset. A range could refer to the **original text** or to the **current text**.

## Strategies

Please contact [Acrolinx SDK support](sdk-support.md) to sign an NDA and get access the list of strategies for lookup.
