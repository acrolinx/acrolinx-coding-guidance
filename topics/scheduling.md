# Scheduling

Acrolinx works for both small and large teams of writers.

In general, you shouldn't have to worry about scaling problems. Acrolinx takes care of this for you.

If you’re planning to significantly increase the load on Acrolinx, talk to Acrolinx Support in advance.
Acrolinx can fine-tune the scalability of your instance.

When building your integration, follow the best practices on communicating with Acrolinx.
Acrolinx will block any unreasonable requests.

Use the following guidelines to minimize issues and maximize the user experience.

## Integration Development Test Instance `partner-dev.acrolinx.sh`

Use [`partner-dev`](https://partner-dev.acrolinx.sh/) to develop your integration.
It's shared among the Acrolinx developer community.
It has limited resources but can handle both integration tests and batch checks.
Since it's a shared instance, use it wisely in respect of other developers.
If possible, submit your check requests in sequential order and avoid too many parallel requests.

## Sidebar

Always first call a `requestCheck` and then call the `check` function (see the [Sidebar API Reference](https://acrolinx.github.io/sidebar-interface/)).
This way the Sidebar controls the frequency of checks.
A user action usually starts a check.

Acrolinx schedules checks from the Sidebar with a high priority (see [Check Types](check-types.md)).
Giving Sidebar checks priority means that users get quick feedback and guidance on their content.

### Lazy Loading of Sidebar

Use lazy loading to reduce the initial load time of the Sidebar.
Efficiency is especially important when each document has its own Sidebar.

The integration environment usually limits the number of simultaneous requests.

If you open many documents at once, the Sidebar might fail to load.
The root cause may be a combination of too many requests and a connection timeout on the integration side.

To avoid this situation, use a lazy load method to load the Sidebar when the user switches to the document.

## Automated and Batch Checks

Design your Acrolinx integration to run smoothly.

By default, batch checking integrations should submit one check after the other.
Set a [Check Type](check-types.md) with a priority below high.

Each integration has its own performance requirements.
If sequential processing is too slow, your admin can configure the number of parallel check requests.
Even if you know the exact resource allocation of an Acrolinx instance, Don't maximize the load to 100%.
Overall performance and user experience can suffer if multiple integrations exceed the maximum load.

In the development phase, consider the number of parallel users the integration will have
and the [checking features](checking-features.md) you implement. How many parallel checks do you expect?

Usually, it's sufficient if you limit the:

* Maximum parallel checks per user.
* Number of cron-based scheduled checks that are executed in parallel.
