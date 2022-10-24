# Template

Use this document template to record your findings and decisions during the PoC.

The following sections will help you get the most out of the effort spent on a proof of concept.

## Title & Summary

* PoC + the name of the host application

## Motivation

* Why are you investing this PoC?
* Who is interested in integrating into this application:
    1. Strategic?
    2. Several customers?
    3. One customer?
    4. Customer / process specific?

## Demo

* Screenshot of the PoC in action
* A short screen cast showing the main functionality, issues, and limitations

*The demo can still be a bit broken. It should be in a format that you can share with others to demonstrate and further discussion.*
*It must [not show sensitive information](security-safety.md).*

## Installation

* Is there an [installation package](packaging.md)? If yes, link it.
* How to install the PoC?

## Request Format

* Link to a check request + result (Scorecard) that is accessible for a couple of months, or
* Attach a check request.txt
* Is that the final request format? If not, document and create a ticket.

## Source Code

* What's the repo URL of the PoC?
* Ideally the first steps for a proper [project setup](project-setup.md) are already done.
* The [`Readme.md`](project-setup.md#readme) of the project should contain how to compile and debug the PoC.

## Limitations, Findings, & Implications

* What are the main limitations?

* Is the host application API feature-complete?
* Will the integration have a user interface or will it just be an embedded integration, or both?

See: [Checking Features](checking-features.md)

* Is it feasible to show the Sidebar?
* Is it possible to [extract the text including document structure](text-extraction.md)?
* Can a text be selected programmatically?
* Can the text be replaced programmatically?
* What is the best lookup strategy?
* How will the integration be deployed, shipped, or packaged?
* How does the [authentication and server configuration](configuration.md) work?
* Which of the following [will be supported](interoperability.md)?
    + platforms,
    + SDKs,
    + browsers,
    + host editor versions, and
    + operating systems
* Which file formats does the host editor support?
* Will it be easy to [build, debug](project-setup.md#build-system), and [test automatically](testing.md)?
* Is any infrastructure missing?
* Are there any [slow API calls that might cause a performance issue](performance.md) later?
    + How much time does the extraction take on a 1, 10, 50, and 100 page document?
    + How quick is the [lookup](text-lookup.md) on these documents?

## Summary

A short executive summary containing:

* How much effort will it require to develop?
* Which technology should be used?
* Describe different levels of scope for an integration.
* Are there any blockers?

## Next Steps

* What is the next logical step?
* What needs to be done to make a product out of the PoC?
