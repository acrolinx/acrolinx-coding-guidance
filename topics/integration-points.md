# Integration Options

Before you add Acrolinx to your application, you'll need to decide where and how to embed Acrolinx.

Acrolinx checks content in two ways:

* An Automated Check helps you automate your content creation workflow.
* The Sidebar gives writers an interactive user experience in the editor where they create content.

---
**NOTE**
How users [authenticate](configuration.md#Authentication) with Acrolinx informs the [check type](check-types.md).

---

![Overview of Integration Options](images/integration-types.png)

## Sidebar (Interactive Direct)

* Purpose:
    + The simplest way to integrate Acrolinx.
    + The Sidebar is perfect for creating a proof of concept.
    + Check content at creation time.
    + If your CMS can't connect to the Acrolinx Platform, the Sidebar might be your only option.
    For example, the CMS is only available within a company's network, but the Acrolinx Platform runs in the cloud.
* Connection: Direct
  Your web browser must be able to reach the Acrolinx Platform.
* Authentication (No attention is required on the integration side):
    + Acrolinx
    + External
    + Federated
* The administrator sets the [Acrolinx URL](configuration.md#Acrolinx-URL).

## Sidebar (Interactive SSO)

* Purpose:
    + The recommended and most convenient way for writers who use a Web CMS.
* Connection: With a reverse proxy on the CMS backend.
* Authentication:
    + SSO
* Set the [Acrolinx URL](configuration.md#Acrolinx-URL) on the CMS backend.

## Automated Check (with a trigger)

* Purpose:
    + Acrolinx automatically checks every document that is updated or saved.
      The data in the Acrolinx Analytics is always up to date without manual action.
* Connection: The CMS backend connects directly to the Acrolinx Platform. You can use one of the Acrolinx Platform SDKs.
* Authentication:
    + SSO: Use either the signed in user or the last editor of the content. Usually it's the same person. (recommended)
    + API token
* Set the [Acrolinx URL](configuration.md#Acrolinx-URL) on the CMS backend.
* The check type depends on the authentication:
    + Automated (recommended) for SSO
    + Baseline for API token

## Automated Check (scheduled)

* Purpose:
    + Sometimes it's not feasible to set up a trigger-based check.
    + Even if you have an interactive integration point, it still makes sense to check all of your content from time to time.
      It will help you stay on top of changes to terminology or configuration.
    + The data in the Acrolinx Analytics is always up to date without manual action.
* Connection: The CMS backend connects directly to the Acrolinx Platform. You can use one of the Acrolinx Platform SDKs.
* Authentication:
    + SSO (recommended)
    + API token
* Set the [Acrolinx URL](configuration.md#Acrolinx-URL) on the CMS backend.
* The check type depends on the authentication:
    + Automated (recommended) for SSO
    + Baseline for API token

## View (Semi-Automated)

* Purpose:
    + Check only some documents.
    + Create a dedicated Content Analysis Dashboard for a portion of your content.
    + Manually start a recheck of your content after configuration or terminology has changed.
* Connection: The CMS backend connects directly to the Acrolinx Platform. You can use one of the Acrolinx Platform SDKs.
* Authentication:
    + SSO (recommended)
    + API token
* Set the [Acrolinx URL](configuration.md#Acrolinx-URL) on the CMS backend.
* The check type depends on the authentication:
    + Baseline (recommended)
    + Batch - if it's clear that the user that starts the check owns the content.

## Sidebar

* Purpose:
    + That's the standard integration in a stand-alone application.
      Technically it's quite similar to [Sidebar (Interactive Direct)](## sidebar-interacrtive-direct).
* Connection: Direct 
  The integration must be able to reach the Acrolinx Platform.
* Authentication (No special handling is required on the integration side):
    + Acrolinx authentication
    + External Authentication
    + Federated Authentication
* You can set the [Acrolinx URL](configuration.md#Acrolinx-URL) with an installer parameter or a deployed configuration.
  Normally, a user would enter it themselves.
* The check type is interactive.

Hint: A lightweight alternative to a full integration is the [Acrolinx Desktop Checker](https://docs.acrolinx.com/desktopchecker/latest/en).

## Batch

* Purpose:
    + Check a set of documents at a time.
    + Provide a lightweight way of analyzing your content without coding.
    + Proof of concept
* Connection: Direct
  The integration must be able to reach the Acrolinx Platform.
* Authentication:
    + Acrolinx authentication
    + External Authentication
    + Federated Authentication
    + API token
* The user enters the [Acrolinx URL](configuration.md#Acrolinx-URL).
  It might also be provided by a script.
* The check type is:
    + Batch (default) if the user owns the documents
    + Baseline if other users documents are checked.

Instead of an Acrolinx SDK, use the [Acrolinx Command Line Interface](https://docs.acrolinx.com/cli/latest/en),
a highly scriptable solution designed for batch checking.
You can also use the [Content Analyzer 2019](https://docs.acrolinx.com/ca/latest/en) to manually check a set of documents.
