# Submitting an SDK Support Ticket

Acrolinx tries to provide the best possible consulting for your integration project.
To help aid in efficient communication, we ask you to provide some contextual information.

## Email Address

* [Acrolinx SDK Support](sdk-support@acrolinx.com): sdk-support@acrolinx.com

Don't use an Acrolinx employee's email address.
They might be on vacation and you won't receive a response.
Instead, always use an email address that goes to the Acrolinx Support ticket system.
If you use the wrong address, we'll forward the email to the right person or system, but it might take some time.

If you're a customer and a certified integration is causing a problem, create a normal support ticket.
The vendor who owns the integration should contact SDK support. We'll link the tickets.
While the integration developers investigate the root cause, Acrolinx Support can provide a solution.

| Topic                                                                    | Action                                                                                                                                                                                                                                                                                                                                                                        | Address                                       |
| ------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------- |
| I'm a customer and a third-party integration isn't working as expected. | Contact vendor support                                                                                                                                                                                                                                                                                                                                                        | Vendor support address + support@acrolinx.com |
| I'm a partner and a customer has filed a support ticket.                 | If the solution isn't obvious or you identified an issue on the Acrolinx side, contact SDK support.                                                                                                                                                                                                                                                                          | sdk-support@acrolinx.com                      |
| The Acrolinx URL that I'm using seems to be down.                        |                                                                                                                                                                                                                                                                                                                                                                               | support@acrolinx.com                          |
| I want to start a new integration project.                               | See [First Contact](#first-contact)                                                                                                                                                                                                                                                                                                                                           | sdk-support@acrolinx.com                      |
| I finished my development work.                                          | See [Certification Meeting](#certification-meeting)                                                                                                                                                                                                                                                                                                                           | sdk-support@acrolinx.com                      |
| While coding, I ran into some problems.                                  | Check for answers to your question in the [Coding Guidance](../README.md), [samples on GitHub](https://github.com/acrolinx?q=demo), [log files](https://github.com/acrolinx/acrolinx-coding-guidance/blob/master/topics/logging.md#path-and-filename), or [FAQ](https://support.acrolinx.com/hc/en-us/sections/201158052-Integrations-FAQs-and-Troubleshooting). | sdk-support@acrolinx.com                      |

## Required Information

Try to include this information with all inquiries:

1. Integration name and version
2. Urgency
3. Screenshots of the problem and the integration
4. Error message
5. [Log files](https://github.com/acrolinx/acrolinx-coding-guidance/blob/master/topics/logging.md#path-and-filename)
6. Platform URL
7. Platform Version
8. Editor Version
9. CMS Name and Version
10. Link to the Scorecard or information captured using the [Request Validator](https://docs.acrolinx.com/kb/en/how-to-use-the-request-validator-13730818.html):
    + `request.txt`
    + `request.properties`
    + Scorecard
    + JSON report
11. Coding language
12. Technology stack
13. Acrolinx SDK and sample it's based on.
14. Can you reproduce the issue using one of our GitHub samples?
15. Can you share a minimal code example that is sufficient to reproduce the issue?

## First Contact

Before you start an integration project, we prefer to schedule a kick-off meeting to provide consulting.
[Getting Started with Custom Integrations](https://docs.acrolinx.com/customintegrations)
summarizes integration options and the process of developing an integration.
This information will help you ask the right questions during the kick-off.
Have you already thought about a [Proof of Concept](poc.md)?

## Certification Meeting

* Have you completely finished the integration? Or do you still have open technical questions?
* Have you [verified](checklist.md) that everything is done?
  Complete the [minimal certification requirements](minimal-requirements.md).
* Share a link to a Scorecard. We'll use the
  [request validator](https://docs.acrolinx.com/kb/en/how-to-use-the-request-validator-13730818.html)
  to analyze the request and identify any issues.
* Are you prepared to give a demo during the meeting?

### Minimal Certification Requirements

See the [Minimal Certification Requirements](minimal-requirements.md).
