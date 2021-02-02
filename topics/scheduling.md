# Scheduling and Scaling

Acrolinx allows large-scale deployments.

If your integration is communicating with the Acrolinx Platform cloud you usually don't have to worry much about scaling.

If you’re planning to increase the load to the Acrolinx Platform significantly, talk to the Acrolinx Support in advance.
That allows Acrolinx to fine-tune the scaling for your instance in advance.

See Also: [How Do I set up Acrolinx to scale to a large number of users?](https://docs.acrolinx.com/kb/en/how-do-i-set-up-acrolinx-to-scale-to-a-large-number-of-users-13730796.html)

Acrolinx expects integrations to communicate to the Core Platform in a cooperative way.
Nevertheless, unsuitable requests will be blocked by the Acrolinx Platform.

Here are some guidelines, about the way to implement integrations in order to minimize issues and maximize the user experience.

See also: [Performance](performance.md)

## Integration Development Test Instance `test-ssl.acrolnx.com`

[`Test-ssl`](https://test-ssl.acrolnx.com) can be used for integration development.
Test-ssl is a shared resource with fixed resource allocation.
The assigned resources are high enough to run integration tests as well as batch checks.
However since it's a shared resource please be respectful of others. Use it in a cooperative mode.
If possible, submit check requests in a sequential order and avoid too many parallel requests.

## Sidebar

The `check`-function should be only called after a `requestCheck` function has been called (See: [Sidebar API Reference](https://acrolinx.github.io/sidebar-interface/)).
This way the Sidebar controls the frequence of checks.
Usually a check is started by a user action.

Checks started by the Sidebar are scheduled with high priority (See [Check Types](check-types.md)).
This allows for quick feedback and guidance about the content to the user.

### Lazy Sidebar Loading

The Sidebar itself should be loaded in a lazy manner.
This is especially important in cases where each document has its own Sidebar instance.

Usually the environment in which integrations run is limiting the number of simultaneous requests.

If a large number of documents are loaded simultaneously loading of the Sidebar might fail.
The root cause might be a combination of maximum request, and connection timeout on the integration-side.

To avoid this situation, load the Sidebar in a lazy manner once the user switches to the document.

## Automated / Batch Processing

Acrolinx Integrations should be designed to run smoothly both in a cloud environment as well as on premise.
Cloud environments can usually deal with high load and additional resources can be allocated.
On-premise set ups are often installed on real hardware that can't be easily scaled.

By default batch checking integrations should submit one check after the other.
A [Check Type](check-types.md) with a priority smaller than high should be used.

Each integration has its own performance requirements.
If sequential processing is too slow, configure as an admin the number of parallel check requests.
Please keep in mind that you shouldn't try to maximize the load to 100%.
Even if you know the exact resource allocation of an Acrolinx Core Platform instance.
If multiple integrations maximize the load, it could easily lead a slow overall performance and negative user experience.

While implementing consider the number of parallel users of the integration,
and the [points where your integration integrates to](integration-points.md). How many parallel checks do you expect?

Usually it's sufficient, if you:

* Limit the maximum parallel checks per user.
* Take care to limit the number of cron based checks that are executed in parallel.
