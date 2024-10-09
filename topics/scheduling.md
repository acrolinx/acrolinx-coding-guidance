# Scheduling

Acrolinx works for both small and large teams of writers.

You shouldn't have to worry about scaling problems. Acrolinx takes care of this for you.

But if you’re planning to significantly increase the checking load, talk to Acrolinx Support.
We can fine-tune the scalability of your instance.

When you build your integration, follow the best practices for communication with Acrolinx.

Use the following guidelines to minimize issues and maximize your user experience.

## Integration development instance `partner-dev.acrolinx.sh`

Use the Acrolinx [`partner-dev`](https://partner-dev.acrolinx.sh/) instance to develop your integration.
It's shared among the Acrolinx developer community.
Its resources are limited but it can handle both integration tests and batch checks.
Since it's a shared instance, use it wisely in respect of other developers.
If possible, submit your check requests in sequential order and avoid too many parallel requests.

## Sidebar

Always first call a `requestCheck` and then call the `check` function (see the [Sidebar API reference](https://acrolinx.github.io/sidebar-interface/)).
This way the Sidebar controls the frequency of checks.
A user action usually starts a check.

Acrolinx schedules checks from the Sidebar with a high priority (see [Check types](check-types.md)).
Giving Sidebar checks priority means that users get quick feedback and guidance on their content.

### Lazy loading of Sidebar

Use lazy loading to reduce the initial load time of the Sidebar.
Efficiency is especially important if each document gets its own Sidebar.

The integration environment usually limits the number of simultaneous requests.

If you open too many documents at once, the Sidebar might fail to load.
The cause may be a combination of too many requests and a connection timeout on the integration side.

To avoid this situation, use a lazy load method to load the Sidebar when the user switches to a document.

## Automated and batch checks

Design your Acrolinx integration to run smoothly.

By default, batch checking integrations should submit one check after the other.
Set a [check type](check-types.md) with a priority less than 'high'.

Each integration has its own performance requirements.
If sequential processing is too slow, contact Acrolinx support to configure the number of parallel check requests.
Even if you know the exact resource allocation of an Acrolinx instance, don't maximize the load to 100%.
Overall performance and user experience can suffer if multiple integrations exceed the maximum load.

While you are developing, consider the number of parallel users the integration will have
and the [checking features](checking-features.md) you implement. How many parallel checks do you expect?

Usually, it's sufficient if you limit the:

* Maximum parallel checks per user.
* Number of cron-based scheduled checks that are executed in parallel.
