# Initialization

## `clientComponents`

While initializing SDKs, make sure that information about the integration and its environment is set properly.
Some of the SDKs use reflection to do that job for you in case all your libraries provide the right information.
In this case, you just have to ensure that all information propagated properly.

The provided information is used in:

* about,
* [logging](logging.md),
* requests send to server,
* [identification of Content Profile](text-extraction.md#how-acrolinx-reads-your-content),
* Scorecards,
* Content Groups,
* analytics,
* etc.

Make sure:

* All components have unique ids in the list.
* Exactly one main component is set.
* No category (default), or `"category": "DETAIL"` can be added as much as useful.
  Keep in mind that this could blow up about or [logging](logging.md).
* The main component is the Acrolinx Integration.
* The Integration is [named correctly](project-setup.md#naming-of-the-integration).
* The list of `clientComponents` contains the host editor, and its version, and has no `category`.
* An id should contain the company name.
  It should be structured similar to [java package naming](formatting.md#java) like `<TOP_LEVEL_DOMAIN>.<DOMAIN>.<PRODUCT>`.
* Suggestion: Define ids with at least two sub part (split by '.').
* Add important libraries that might influence the behavior of the integration significantly as `"category": "DETAIL"`.
* Same components should get the same ids in all integrations.
* The [version](project-setup.md#version-information)) uses the standardized format.

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