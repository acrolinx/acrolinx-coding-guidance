# Template

This document can be used as template to provide proper documentation and reference for decisions.
It turned out,
that the following sections make sense for getting the most benefit out of the effort spend into making a proof of concept.

## Title/Summary

* PoC + the name of the host editor

## Motivation

* Why should this be elaborated?
* Who is interested in integrating into this editor:
    1. Strategic?
    2. Several customers?
    3. One customer?
    4. Customer / process specific?

## Demo

* Screenshot of the PoC in action
* A short screen cast showing the main functionality, probably also issues / limitations

*This can still look a bit broken. It should be in a format that can be shown to others to demonstration and discussion purpose.*
*It must [not show sensitive information](security-safety.md).*

## Installation

* Is there an [installation package](packaging.md)? If yes, link it.
* How to install the PoC?

## Request Format

* Link to a check request + result that is accessible even a couple of months later, or
* Attach a check request.txt
* Is that the final request format? If not, document and create a ticket.

## Source Code

* What's the repo URL of the PoC?
* Ideally already the first steps for a proper [project setup](project-setup.md) are already done.
* The [`Readme.md`](project-setup.md#readme) of the project should contain how to compile, and debug the PoC.

## Limitations / Findings / Implications

* What are the main limitations?
* Is the host editors API feature complete?
* Does the integration will have a user interface, or will it just be an embedded integration, or both?
* Is it feasible to show the Sidebar?
* Is it possible to [extract the text including structure](text-extraction.md)?
* Can a text be selected programmatically?
* Can the text be replaced programmatically?
* What is the best lookup strategy?
* How will the integration be deployed / shipped / packaged?
* How does the [authentication and server configuration](configuration.md) be?
* Which [platforms, SDKs, browsers, host editor versions, and operating systems will be supported](interoperability.md)?
* Which file formats does the host editor support?
* Will it be easy to [build, debug](project-setup.md#build-system), and [test automatically](testing.md)?
* Any infrastructure missing?
* Are there any [slow API calls that might cause a performance issue](performance.md) later?
    + How much time takes the extraction on a 1, 10, 50, and 100 pages document?
    + How quick is the [lookup](text-lookup.md) on these documents?

## Summary

A short executive summary containing:

* How much effort will it be?
* Which technology should be used?
* Write a short description, of what are the possible scopes of an integration.
* Are any blockers left?

## Next Steps

* What is the next logic step?
* What needs to be done to make a product out of the PoC?