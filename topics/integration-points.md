# Integration Points

Before integrating Acrolinx into a system it makes sense to decide on the best places to integrate. There are two ways to check the produced content by
* an automated way to ensure certain quality standards.
* integrating Sidebar in the editor to enable interactive user experience where content gets created.

![Overview of the different integration types](images/integration-types.png)

Also consider, how to [authenticate](configuration.md#Authentication) users in an integration? Authentication will influence the recommendation for the [check type](check-types.md).

## Interactive Direct (Sidebar)

* Purpose:
    + That's the simplest way to integrate Acrolinx. It might be used for a proof of concept.
    + Check content at the creation time
    + It could also be the only solution in case the CMS can't connect to the Acrolinx Platform.
    For example the CMS is hosted inside the companies network, but the Acrolinx Platform runs in the cloud.
* Connection: Direct, the web browser must be able to reach the Acrolinx Platform.
* Authentication (No special handling is required on the integration side):
    + Acrolinx authentication,
    + External Authentication,
    + Federate Authentication
* The [Acrolinx URL](configuration.md#Acrolinx-URL) could be prepopulated by the administrator.

## Interactive SSO (Sidebar)

* Purpose:
    + That's the preferred way and most convenient for the writers who are using Web CMS.
* Connection: Through a reverse proxy on the CMS backend.
* Authentication:
    + SSO
* The [Acrolinx URL](configuration.md#Acrolinx-URL) is configured in the backend of the CMS.

## Trigger (Automated)

* Purpose:
    + Every file that is checked in, or saved will be checked automatically.
      The data in the Acrolinx Analytics is always up to date without manual action.
* Connection: The CMS backend connects directly to the Acrolinx Platform. One of the Acrolinx Platform SDKs can be used.
* Authentication:
    + SSO: Use either the signed in user, or the last editor of the content. Typically these are identically. (recommended)
    + API token
* The [Acrolinx URL](configuration.md#Acrolinx-URL) is configured in the backend of the CMS.
* The check type depends on the authentication:
    + Automated (recommended), for SSO,
    + Baseline, for API token

## Cron Job (Automated)

* Purpose:
    + Sometimes it's not feasible to set up a trigger-based approach.
    + Even if other integration points are used it makes sense to check the whole content from time to time.
      It will catch up with changes in terminology or configuration.
    + The data in the Acrolinx Analytics is always up to date without manual action.
* Connection: The CMS backend connects directly to the Acrolinx Platform. One of the Acrolinx Platform SDKs can be used.
* Authentication:
    + SSO (recommended)
    + API token
* The [Acrolinx URL](configuration.md#Acrolinx-URL) is configured in the backend of the CMS.
* The check type depends on the authentication:
    + Automated (recommended), for SSO,
    + Baseline, for API token

## View (Semi-Automated)

* Purpose:
    + Check only some documents.
    + Create a dedicated Content Analysis dashboard for a partition of your content.
    + Manually start a recheck of your content after configuration or terminology has changed.
* Connection: The CMS backend connects directly to the Acrolinx Platform. On of the Acrolinx Platform SDKs can be used.
* Authentication:
    + SSO (recommended)
    + API token
* The [Acrolinx URL](configuration.md#Acrolinx-URL) is configured in the backend of the CMS.
* The check type depends on the authentication:
    + Baseline (recommended),
    + Batch, in case in a use case it's clear that the user that checks own the content.

## Integration (Sidebar)

* Purpose:
    + That's the standard for all integrations in stand-alone application.
      Technically it's quite similar to [Interactive Direct (Sidebar)](#interactive-direct-sidebar).
* Connection: Direct, the integration must be able to reach the Acrolinx Platform.
* Authentication (No special handling is required on the integration side):
    + Acrolinx authentication,
    + External Authentication,
    + Federate Authentication
* The [Acrolinx URL](configuration.md#Acrolinx-URL)
  could be sometimes prepopulated by an installer parameter, or some deployed configuration.
  Normally it's just entered by the user.
* The check type is interactive.

Hint: A lightweight alternative to code a full integration is the [Acrolinx Desktop Checker](https://docs.acrolinx.com/desktopchecker/latest/en).

## Batch Integration

* Purpose:
    + Check a set of files at a time.
    + Provide a lightweight way of analyzing your content without coding.
    + Proof of concept
* Connection: Direct, the integration must be able to reach the Acrolinx Platform.
* Authentication:
    + Acrolinx authentication,
    + External Authentication,
    + Federate Authentication,
    + API token
* The [Acrolinx URL](configuration.md#Acrolinx-URL) it's just entered by the user.
  It might also be provided by a script.
* The check type is:
    + Batch (default), if the user owns the files,
    + Baseline, if other users files are checked.

Instead of an Acrolinx SDK use [Acrolinx Command Line Interface](https://docs.acrolinx.com/cli/latest/en), a highly scriptable solution designed for the batch integration. The [Content Analyzer 2019](https://docs.acrolinx.com/ca/latest/en) could also be used for manual checking a set of files.
