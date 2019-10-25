# Submitting an SDK Support Ticket

Acrolinx tries to provide the best consulting for your integration project.
To avoid back and forth and to be most efficient, it makes sense to provide some information.

## Addressing

* [Acrolinx SDK Support](sdk-support@acrolinx.com): sdk-support@acrolinx.com

Don't use a direct email address of an Acrolinx employee.
They might be on vacation and the request get stuck.
To avoid this use one of the email addresses that end up in our ticket system.
Anyway if you use the wrong address, we'll forward the request to the right person or system, but it might take some time.

If an integration was certified and a problem occurs, it often makes sense to have a normal support ticket field.
In addition, the vendor of the integration should contact SDK support and link to that customer support ticket.
While the integration developers and the SDK nail down the root cause, the support team can provide some solution.

| Topic                                                                    | Action                                                                                                                                                                                                                                                                                                                                                                                                                     | Address                                       |
| ------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------- |
| I'm a customer and the third-party integration doesn't work as expected. | Contact vendor support                                                                                                                                                                                                                                                                                                                                                                                                     | Vendor support address + support@acrolinx.com |
| I'm a partner and a customer has filed a support ticket.                 | If the solution isn't obvious, or you located an issue on the Acrolinx side contact the SDK support.                                                                                                                                                                                                                                                                                                                       | sdk-support@acrolinx.com                      |
| The Acrolinx URL that I'm using seems to be down.                        |                                                                                                                                                                                                                                                                                                                                                                                                                            | support@acrolinx.com                          |
| I want to start a new integration project.                               | See [First Contact](#first-contact)                                                                                                                                                                                                                                                                                                                                                                                        | sdk-support@acrolinx.com                      |
| I finished my development work.                                          | See [Certification Meeting](#certification-meeting)                                                                                                                                                                                                                                                                                                                                                                        | sdk-support@acrolinx.com                      |
| While coding, I ran into some problems.                                  | Check if the [Guidance for the Development of Acrolinx Integrations](../README.md), one of the samples on [GitHub](https://github.com/acrolinx?q=demo), the [log files](https://github.com/acrolinx/acrolinx-coding-guidance/blob/master/topics/logging.md#path-and-filename), or the [FAQ](https://support.acrolinx.com/hc/en-us/sections/201158052-Integrations-FAQs-and-Troubleshooting) already answers your question. | sdk-support@acrolinx.com                      |

## Required Information

Please try to include this information in all requests:

1. Integration name and version
2. Urgency
3. A screenshot of the problem and the integration
4. Error message
5. [Log files](https://github.com/acrolinx/acrolinx-coding-guidance/blob/master/topics/logging.md#path-and-filename)
6. Platform URL
7. Platform Version
8. Editor Version
9. CMS Name and Version
10. Link to the Scorecard, or information captured using the request validator:
    + `request.txt`
    + `request.properties`
    + Scorecard
    + JSON report
11. Coding language
12. Technology stack
13. Acrolinx SDK / Sample it's based on.
14. Is it reproducible using one of our GitHub samples?
15. Can you share a minimal code example that is sufficient to reproduce the issue?

## First Contact

Before you start an integration project, we like to give you some guidance in a so called kick-off meeting.
To be aware of the process and the options have a look at
[Getting Started with Custom Integrations](https://docs.acrolinx.com/customintegrations).
It will help you asking the right questions during the kick-off.
Maybe you want to think about a [Proof of Concept](poc.md) already?

## Certification Meeting

* Have you really finished your integration work, or do you still have open technical questions?
* Have you [ensured](checklist.md) that everything is fine?
* Please share a Scorecard link. We look into the request and analyze in advance using the
  [request validator](https://docs.acrolinx.com/kb/en/how-to-use-the-request-validator-13730818.html),
  if the most prominent mistakes aren't made.
* Are you ready for a demo during the meeting?
