# Initialization

## `clientComponents`

When you initialize SDKs, properly set the information about the integration and its environment.
If all your libraries provide the right information, some of the SDKs pass on the details for you.
Then, you just have to check that all information correctly propagates to the different places.

The information appears in:

* About
* requests sent to Acrolinx
* [content profile selection](text-extraction.md#how-acrolinx-reads-your-content),
* Scorecards
* Content groups
* Reporting

Make sure you:

* Give all components unique IDs.
* Set exactly one main component.
* Only add a category (default) or `"category": "DETAIL"` to the extent useful.
  Keep in mind that this could mess up the About or [logging](logging.md) information.
* Define the Acrolinx integration as the main component.
* [Correctly name](project-setup.md#naming-of-the-integration) the integration.
* Include the host editor and its version in the list of `clientComponents`, but don't define a `category`.
* Define the company name with an ID.
  Structure it similar to the [java package naming](formatting.md#java), such as `<TOP_LEVEL_DOMAIN>.<DOMAIN>.<PRODUCT>`.
* Define IDs with at least two subparts (split by '.'). (suggestion)
* Add important libraries as `"category": "DETAIL"` if they might significantly influence the behavior of the integration.
* Give the same components the same IDs in all integrations.
* Use the standard format for the [version](project-setup.md#version-information)).

### Example

```json
"clientComponents": [
  {
    "id": "com.acrolinx.sidebarexample",
    "name": "Acrolinx for My CMS",
    "version": "1.2.3.999",
    "category": "MAIN"
  },
  {
    "id": "com.company.somecms",
    "name": "My CMS",
    "version": "1.2.3.999"
  },
  {
    "id": "com.acrolinx.somelib",
    "name": "Referenced Lib",
    "version": "1.0.0.0",
    "category": "DETAIL"
  },
  {
    "id": "com.acrolinx.anotherlib",
    "name": "Another Referenced Lib",
    "version": "0.0.0.1",
    "category": "DETAIL"
  }
]
```
