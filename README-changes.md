# Extend functionality of `svc` to be able to send `SIGUSR1` and `SIGUSR2`

The need for additional functionality is described in this [issue](https://github.com/daemontools/daemontools/issues/4).

A corresponding [pull-request](https://github.com/daemontools/daemontools/pull/5).

# Problem:

A _service_ monitored by `supervise` is listening for the signals
`SIGUSR1` and/or `SIGUSR2`. It is expecting these signals which will
trigger actions in the _service_.

While under supervision by *daemontools*, the is no practical way to
send these signals to the _service_.

# Proposed Solution:

The normal way to send signals to a _service_ under supervision is to
use the `svc` program. For example `svc -h /service/myservice` will send
a `SIGHUP` to the _service_.

Augmenting `svc` by adding new options to extend the functionality to
include sending the desired signals will resolve this issue.

The new options `-v` and `-w` are proposed for sending `SIGUSR1` and
`SIGUSR2`, respectively.
