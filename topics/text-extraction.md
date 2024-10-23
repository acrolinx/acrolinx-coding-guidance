# Text extraction

## Input types and integrating with multiformat editors
Before you build an integration, you'll need to understand what input types Acrolinx supports.

Does your application provide the document in a format that Acrolinx supports?

* XML
* HTML

Acrolinx supports different input types:

| Input type                | API setting  | Default extension | Notes             |
| ------------------------- | ------------ | ----------------- | ----------------- |
| Text                      | `TEXT`       | `.txt`            |                   |
| XML                       | `XML`        | `.xml`            |                   |
| HTML                      | `HTML`       | `.html`           |                   |
| JSON                      | `JSON`       | `.json`           |                   |
| Java properties files     | `PROPERTIES` | `.properties`     |                   |
| Markdown                  | `MARKDOWN`   | `.md`             |                   |
| Java Source files         | `JAVA`       | `.java`           | Comments, Javadoc |
| Base64 encoded binary PDF | `PDF`        | `.pdf`            | no offsets        |

See the complete list of [supported input types](https://support.acrolinx.com/hc/en-us/articles/10211264846482-Supported-Input-Types).

When you submit a check using the API or the `sidebar.checkGlobal()` call, specify the format to let Acrolinx know the input
type of the document. You can also set the format to `AUTO`.
Acrolinx uses a pattern that matches the reference and identifies the document type.
Some input types, like DITA or resx, are a subset of the supported input types but have a different file extension.

For multiformat editors, we recommend letting Acrolinx identify the format.

*Note: If possible, use the default
[file mapping](https://support.acrolinx.com/hc/en-us/articles/10211141076882-Configure-Acrolinx-to-Recognize-Your-File-Type)
and content profiles. Content profiles let you configure how Acrolinx reads your content. 

If you need a custom content profile, contact [Acrolinx Support](https://support.acrolinx.com/hc/en-us/requests/new)!*

## Application API with object model

If your application doesn't provide the content in a format that Acrolinx supports,
then you have to implement the text extraction as part of the integration.

The extracted text should be as similar as possible to the object model and correspond to what the user sees on screen.

Acrolinx needs to identify the document type to select the right content profile. To help Acrolinx, follow these best practices:

* Include a schema or a DTD
  
<!DOCTYPE integration name PUBLIC "-//acrolinx integrationname-v1" "integrationname-v1.dtd">

* If you define a schema or a DTD, include the reference in the XML
* If you’re able to define a schema or a DTD, then you specified your format well.

Extraction can look like this:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<!DOCTYPE integrationname PUBLIC "-//acrolinx integrationname-v1" "integrationname-v1.dtd">
<integrationname>
<page no="1">
    <p style="style1" language="en">some text</p>
    <table>
        <row>
            <cell language="en">some text in a table</cell>
        </row>
    </table>
    <somespecialelement>
    </somespecialelement>
    <group>
        <image />
        <textbox style="style2" language="en">some text</textbox>
        <textbox style="style3" visible="false" language="en">some other text</textbox>
        <textbox style="style3" visible="false" language="de">das ist ein test.</textbox>
    </group>
</page>
<page no="2" visible="false">

</page>
</integrationname>
```

The aim is to include all information that Acrolinx needs to analyze the content.

## What's important for text processing

### Document structure

If an element is inside another element or in a group of elements,
show this structure in the converted document.
For an image, figure, or other nontextual elements, create a placeholder with its type name.
Don't send the image to Acrolinx with the document. Acrolinx doesn't need image for text processing.

The order of the elements matters. The position of the elements in these examples is different:

* `<text>This <image /> is nice</text>`
* `<text>This is nice</text><image />`

Acrolinx can treat an image as a “wildcard” so that it won't wrongly highlight a guideline:
Could you use a noun after "this/that/these/those"?
Each element should include information about styles and visibility (users can't see all content).

Acrolinx relies on this structural and contextual information to know which parts of a document belong together.

#### Example of structural information

Depending on the structural information included with the content, a sentence like "This is a text." may be correct or incorrect:

Incorrect:

```html
<p>This is</p> <p>a text.</p>
```

Correct:

```html
<p>This is a text.</p>
```

It's important to maintain as much structure of the original document as possible.
Otherwise, Acrolinx can’t detect these kinds of issues.

### Contexts

The document should include information about the tags, styles, or fonts in which the text appears.
Acrolinx uses contextual information to filter and extract content and decide which guidelines to apply.
You can configure context information with element names, attributes, or attribute values.

#### Extraction settings

Setting the starting element to `include` works for most cases. This means that Acrolinx will read everything.

If you set the starting element to `exclude`, Acrolinx won’t read anything.

Filter Mode:

You can also define elements as `empty`.
Acrolinx filters out empty elements but assumes that the correct word is at this position.
Defining an empty element is often the only choice if includes or references are non-resolvable.

Break Level:

* `sentence`: has the same effect as if it's at the beginning of a new paragraph
* `none`: ignores the context change
* `token`: treats it like a word boundary
* `parenthetic`: Acrolinx checks parenthetic elements separately and not in the context in which they occur in the request text.

#### Read-only text

It's also feasible to define contexts as `read-only`.
If an issue occurs in a ready-only part of a document, then the corresponding Sidebar card will also appear as read-only.
If an integration uses includes, references, locked, or write-protected text, you'll want the Sidebar cards to appear
as read-only.

#### Attributes

Acrolinx reads attribute values, but Sidebar integrations can't always provide full lookup support. This means the Sidebar
can't navigate to the issue text or automatically replace suggestions.

#### Example of contextual information

Write title text in AP (Associated Press) style:

```xml
<title>Nice Title to Show how Relevant the Style Name is</title>
```

Sentence case calls for first word uppercase and the rest lowercase:

```html
<p>This normal text requires a dot at the end of the sentence.</p>
```

## Acrolinx guidance and analytics

1. Send the file name, URI, or a unique reference to the source document.
   - This information helps Acrolinx uniquely identify each document.
   - A unique reference helps Acrolinx users find their content in the CMS, on the hard drive, or wherever it came from.
2. Set a DOCTYPE, a root element, or both so that Acrolinx can apply the right extraction.
3. Use the recommended [check type](check-types.md).

## What's a document

It's not always obvious what information developers should include in a check request.
Acrolinx calculates scores for documents, provides guidance, and visualizes analytics dashboards.
For all of these cases, it's important to submit the right chunk of content.

A CCMS uses several sources and generates one or more documents from the same content.
For example, an XML DITA map references different topics that create a larger document.
Customers might use this same DITA map to generate one PDF manual or several web pages.
In this way, they assemble the same content differently for different purposes.

* If the published content is one document (for example PDF), then you should submit the entire content as one request.
* If the published content is several web pages, then you should submit the content as separate requests so Acrolinx
  checks and scores each page individually.

### Document scope characteristics

* The content has a unique reference.
* The reference is stable.
* The size of the content is exactly what gets published later.
* All content topics, or paragraphs, have the same audience (group of readers).

## Check selection

The Acrolinx Sidebar can only show issue cards for the text that a writer selects at check time.
To enable the check selection feature, set the property `InitParameters.supported.checkSelection: true`.
During text extraction, use the property `CheckOptions.selection.ranges:[[0,5], [400,500]]` to set the selected range
offsets of the extracted text.

To figure out the range offsets, you might need to do a mapping between the application offsets and extraction offsets.
This might be a reverse [implementation of the lookup](text-lookup.md).

*Note: If you use an Acrolinx SDK, then the check selection feature might work as expected without you having to implement anything.*
*Read the SDK API to learn more about check selection.*
