---
title: Acrolinx checking features
description: Learn about checking features for integrating Acrolinx.
keywords: checking features, automated check, Sidebar, batch check 
---

# Acrolinx checking features

Before you add Acrolinx to your application, you'll need to decide where and how to do it.

Acrolinx checks content in two ways:

* An automated check helps you automate your content creation workflow.
* The Sidebar gives writers an interactive user experience in the editor where they create content.

---
**NOTE**
How users [authenticate](authentication.md#Authentication) with Acrolinx informs the [check type](check-types.md).

---

![Overview of checking features](images/checking-features.png)


## Sidebar - interactive direct

* Uses:
    + Simplest way to integrate Acrolinx.
    + Perfect for creating a proof of concept.
    + For writers to check content at creation time.
    + If the CMS can't connect to Acrolinx, the Sidebar might be your only option.
    + If the CMS is only available within your company's network.
* Connection:
    + Direct
    + Make sure your web browser can reach Acrolinx.
* Authentication (nothing to do on the integration side):
    + Acrolinx
    + External
    + Federated
* Administrator sets the [Acrolinx URL](authentication.md#Acrolinx-URL).

## Sidebar - interactive SSO

* Uses:
    + Most convenient and recommended way for writers who use a web CMS.
* Connection:
    + Use a reverse proxy on the CMS backend.
* Authentication:
    + SSO
* Set the [Acrolinx URL](authentication.md#Acrolinx-URL) on the CMS backend.

## Automated check on an event

* Uses:
    + Automatically check every document on update or save.
    + A suite of dashboards helps you assess performance, identify problems, and improve your content.
* Connection:
    + CMS backend connects directly to Acrolinx.
    + Use an automation SDK.
* Authentication:
    + SSO: Use the signed in user or the last user who edited the content. Usually it's the same person. (recommended)
    + API token
* Set the [Acrolinx URL](authentication.md#Acrolinx-URL) on the CMS backend.
* Check type depends on the authentication:
    + Automated (recommended) for SSO
    + Baseline for API token

## Automated check - scheduled

* Uses:
    + It's not always feasible to automate a check on an event.
    + If you use an interactive integration, you still might want to occasionally check your content as a whole.
    + Automatically check your content after you update terminology or guidelines.
    + A suite of dashboards helps you assess performance, identify problems, and improve your content.
* Connection:
    + CMS backend connects directly to Acrolinx.
    + Use an automation SDK.
* Authentication:
    + SSO (recommended)
    + API token
* Set the [Acrolinx URL](authentication.md#Acrolinx-URL) on the CMS backend.
* Check type depends on the authentication:
    + Automated (recommended) for SSO
    + Baseline for API token

## View - Semiautomated

* Uses:
    + Check a batch of documents.
    + Create a dedicated Content Analysis Dashboard for a subset of content.
    + Manually check your content after you update terminology or guidelines.
* Connection:
    + CMS backend connects directly to Acrolinx.
    + Use an automation SDK.
* Authentication:
    + SSO (recommended)
    + API token
* Set the [Acrolinx URL](authentication.md#Acrolinx-URL) on the CMS backend.
* Check type depends on the authentication:
    + Baseline (recommended)
    + Batch - if the user that starts the check owns the content.

## Sidebar

* Uses:
    + Standard way of using Acrolinx in a standalone application.
    + Technically similar to [Sidebar - interactive direct](#sidebar---interactive-direct).
* Connection:
    + Direct
    + Make sure your integration can reach Acrolinx.
* Authentication (nothing to do on the integration side):
    + Acrolinx
    + External
    + Federated
* Set the [Acrolinx URL](authentication.md#Acrolinx-URL) with an installer parameter or a deployed configuration.
    + Users normally enter the Acrolinx URL themselves.
* Check type is interactive.

Hint: You can also use the [Acrolinx Desktop Checker](https://support.acrolinx.com/hc/en-us/sections/20389701192978-Desktop-Checker) instead of building
a full-featured integration.

## Batch

* Uses:
    + Check a set of documents in bulk.
    + An easy way of analyzing your content without coding.
    + Proof of concept.
* Connection:
    + Direct
    + Make sure your integration can reach Acrolinx.
* Authentication:
    + Acrolinx
    + External
    + Federated
    + API token
* Users enter the [Acrolinx URL](authentication.md#Acrolinx-URL).
    + You can also use a script to set the Acrolinx URL.
* Check type:
    + Batch (default) if the user owns the documents.
    + Baseline if checking other users' documents.

Instead of using an Acrolinx SDK, consider the [Command Line Interface](https://support.acrolinx.com/hc/en-us/sections/10210853773970-Command-Line-Interface-CLI-).
It's a highly scriptable solution designed for batch checking.
You can also use the [Content Analyzer](https://support.acrolinx.com/hc/en-us/sections/10210712471442-Content-Analyzer) to manually check a set of documents.
