yarn-logs-helpers (for kerberos)
=================
Scripts for parsing / making sense of yarn logs.

# Contents
#### `yarn-container-logs`
The main script of note here is [`yarn-container-logs`](https://github.com/hammerlab/yarn-logs-helpers/blob/master/yarn-container-logs):

```
$ source yarn-logs-helpers/.yarn-logs-helpers.sourceme
$ YARN_LOGS_USER=someone yarn-container-logs application_1416279928169_0018
```
*  It downloads the YARN logs for that application into a local directory (defaulting to the application ID, but can be overriden with an optional second argument, after the app ID) and splits them into per-container files:

    ```
    # Directory created by yarn-container-logs
    $ cd application_1416279928169_0018

    # Directory with per-container logs
    $ cd containers

    # Per-container log files have prefix /container_/
    $ ls container_*
    container_1416279928169_0018_01_000015
    container_1416279928169_0018_01_000016
    container_1416279928169_0018_01_000017
    ...

    # The files contain exactly what was pulled down from YARN.
    $ head container_1416279928169_0018_01_000015
    Container: container_1416279928169_0018_01_000015 on my-node-11-10.rest.of.domain.name_port
    ===================================================================================================
    LogType: stderr
    LogLength: 700
    Log Contents:
    ...

# Installing
Download this repository with:

        git clone --recursive https://github.com/louie5486/yarn-logs-helpers.git

        $ cd yarn-logs-helpers

        $ source .yarn-logs-helpers.sourceme

