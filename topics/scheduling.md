# Scheduling and Scaling

Acrolinx allows large-scale deployments.

If your integration is communicating with the Acrolinx Platform cloud you usually don't have to worry much about scaling.

If you’re planning to increase the load to the Acrolinx Platform significantly, talk to the Acrolinx Support in advance.
That allows to fine-tune the scaling for your instance in advance.

See Also: [How Do I set up Acrolinx to scale to a large number of users?](https://docs.acrolinx.com/kb/en/how-do-i-set-up-acrolinx-to-scale-to-a-large-number-of-users-13730796.html)

Acrolinx expects integrations to communicate to the Core Platform in a cooperative way.
Nevertheless, unsuitable requests will be blocked by the Acrolinx Platform.

Here are some guidelines, how integrations should be implemented to minimize issues and maximize the user experience.

See also: [Performance](performance.md)

## Integration Development Test Instance `test-ssl.acrolnx.com`

The test instance [`test-ssl`](https://test-ssl.acrolnx.com) that is used for integration development.
The instance is a shared resource with fixed resource allocation.
The assigned resources are high enough to run integration tests as well as batch checks.
Since it's a shared resource please be respectful and use it in a cooperative mode.
If possible submit check requests in a sequential order and avoid too many parallel requests.

## Sidebar

The `check`-function should be only called after a `requestCheck` function has been called (See: [Sidebar API Reference](https://acrolinx.github.io/sidebar-interface/)).
This way the Sidebar controls the frequence of checks.
Usually a check is started by a user action.

Checks started by the Sidebar are scheduled with high priority (See [Check Types](check-types.md)).
This allows quick feedback and guidance about the content to the user.

### Lazy Sidebar Loading

The Sidebar itself should be loaded lazy.
This is especially important in case each document has its own Sidebar instance.
If a huge number of documents are loaded simultaneously (for example, restore last session)
the number of requests could be high.

Usually the environment where integrations run is limiting the number of simultaneous requests.
That might cause client-side hick ups.

Avoid those hiccups by lazy loading of the Sidebar once the user switches to the document.

## Automated / Batch Processing

Acrolinx Integrations should be designed in a way that they can run in a cloud environment as well as on premise.
Cloud environments can usually deal with high load and additional resources can be allocated.
On-premise set ups are often installed on real hardware that can't be easily scaled.

By default batch checking integrations should submit one check after the other.
A [Check Type](check-types.md) with a priority smaller than high should be used.

Each integration has its own performance requirements.
If sequential processing is too slow, add an admin configuration for the number of parallel check requests.
If you know the exact resource allocation of an Acrolinx Core Platform instance,
please keep in mind that you shouldn't try to maximize the load to 100%.
If multiple integrations maximize the load, it could easily lead a slow overall performance and bad user experience.

While implementing consider the number of parallel users of the integration,
and the [points where your integration integrates to](integration-points.md). How many parallel checks do you expect?

Usually it's sufficient, if you:

* Limit the maximum parallel checks per user.
* Take care that not too many cron based checks are executed in parallel.
