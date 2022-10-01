# Integration Options

Before you add Acrolinx to your application, you'll need to decide where and how to embed Acrolinx.

Acrolinx checks content in two ways:

* Automated Check helps you automate your content creation workflow.
* The Sidebar gives writers an interactive user experience in the editor where they create content.

---
**NOTE**
How users [authenticate](configuration.md#Authentication) with Acrolinx informs the [check type](check-types.md).

---

![Overview of Integration Options](images/integration-types.png)

## Sidebar - Interactive Direct

* Benefits:
    + Simplest way to integrate Acrolinx.
    + The Sidebar is perfect for creating a proof of concept.
    + Writers check content at creation time.
    + If your CMS can't connect to the Acrolinx Platform, the Sidebar might be your only option.
    + For example, the CMS is only available within your company's network, but the Acrolinx Platform runs in the cloud.
* Connection:
    + Direct
    + Your web browser must be able to reach the Acrolinx Platform.
* Authentication (no attention required on the integration side):
    + Acrolinx
    + External
    + Federated
* Administrator sets the [Acrolinx URL](configuration.md#Acrolinx-URL).

## Sidebar - Interactive SSO

* Benefits:
    + Recommended and most convenient way for writers who use a Web CMS.
* Connection:
    + Use a reverse proxy on the CMS backend.
* Authentication:
    + SSO
* Set the [Acrolinx URL](configuration.md#Acrolinx-URL) on the CMS backend.

## Automated Check on an Event

* Benefits:
    + Automatically check every document on update or save.
    + Use Acrolinx Analytics dashboards to assess performance and optimize your content operation.
* Connection:
    + CMS backend connects directly to the Acrolinx Platform.
    + Use one of the Acrolinx Platform SDKs.
* Authentication:
    + SSO: Use the signed in user or the last user who edited the content. Usually it's the same person. (recommended)
    + API token
* Set the [Acrolinx URL](configuration.md#Acrolinx-URL) on the CMS backend.
* Check type depends on the authentication:
    + Automated (recommended) for SSO
    + Baseline for API token

## Automated Check - Scheduled

* Benefits:
    + Sometimes it's not feasible to set up a check on an event.
    + Even if you have an interactive integration point, it still makes sense to check all of your content from time to time.
    + Automatically check your content after updating terminology or guidelines.
    + Use Acrolinx Analytics dashboards to assess performance and optimize your content operation.
* Connection:
    + CMS backend connects directly to the Acrolinx Platform.
    + Use one of the Acrolinx Platform SDKs.
* Authentication:
    + SSO (recommended)
    + API token
* Set the [Acrolinx URL](configuration.md#Acrolinx-URL) on the CMS backend.
* Check type depends on the authentication:
    + Automated (recommended) for SSO
    + Baseline for API token

## View - Semiautomated

* Benefits:
    + Check only some documents.
    + Create a dedicated Content Analysis Dashboard for a portion of your content.
    + Manually check your content after updating terminology or guidelines.
* Connection:
    + CMS backend connects directly to the Acrolinx Platform.
    + Use one of the Acrolinx Platform SDKs.
* Authentication:
    + SSO (recommended)
    + API token
* Set the [Acrolinx URL](configuration.md#Acrolinx-URL) on the CMS backend.
* Check type depends on the authentication:
    + Baseline (recommended)
    + Batch - if the user that starts the check owns the content.

## Sidebar

* Benefits:
    + Standard way of using Acrolinx in a stand-alone application.
    + Technically similar to [Sidebar (Interactive Direct)](integration-points.md#interactive-direct-sidebar).
* Connection:
    + Direct
    + Integration must be able to reach the Acrolinx Platform.
* Authentication (No attention required on the integration side):
    + Acrolinx authentication
    + External Authentication
    + Federated Authentication
* You can set the [Acrolinx URL](configuration.md#Acrolinx-URL) with an installer parameter or a deployed configuration.
  Normally, a user would enter it themselves.
* Check type is interactive.

Hint: A lightweight alternative to a full integration is the [Acrolinx Desktop Checker](https://docs.acrolinx.com/desktopchecker/latest/en).

## Batch

* Benefits:
    + Check a set of documents at a time.
    + Provide a lightweight way of analyzing your content without coding.
    + Proof of concept
* Connection:
    + Direct
    + Integration must be able to reach the Acrolinx Platform.
* Authentication:
    + Acrolinx
    + External
    + Federated
    + API token
* User enters the [Acrolinx URL](configuration.md#Acrolinx-URL).
    + You can also set it with a script.
* Check type is:
    + Batch (default) if the user owns the documents.
    + Baseline if checking other users' documents.

Instead of using an Acrolinx SDK, consider the [Acrolinx Command Line Interface](https://docs.acrolinx.com/cli/latest/en).
It's a highly scriptable solution designed for batch checking.
Or you can use the [Content Analyzer 2019](https://docs.acrolinx.com/ca/latest/en) to manually check a set of documents.
