---
layout: section
---

<i class="fas fa-cogs icon fa-7x"></i>

<br/>
<br/>
<br/>

# Configurations

The configuration files location will vary depending on whether you've set up an XDG environments.
For the following sections, let's assume we've set these [XDG](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html) environment variables to override the default locations:

```shell
export XDG_CONFIG_HOME=$HOME/.config
export XDG_CACHE_HOME=$HOME/.cache
export XDG_STATE_HOME=$HOME/.local/state
```

K9s configurations are divided into two main groups:

1. Global contains general settings and defaults
2. Context specifies configurations to target a given Kubernetes context

Global configurations reside in `$HOME/.config/k9s-alpha` and contains the following files:

| File               |  Description                                                  |
| :----------------- | :------------------------------------------------------------ |
| aliases.yaml       | Defines custom resource aliases                               |
| config.yaml        | Defines the main application settins and defaults             |
| default-skins.yaml | The primordial skins theme                                    |
| hotkeys.yaml       | Specifies keysboard shortcuts for faster resource traversals  |
| license.yaml       | Contains your application license key                         |
| plugins.yaml       | Defines plugins definitions and activation keyboard shortcuts |
| views.yaml         | Provides for resource views custom column definitions         |

Context configurations reside in `$HOME/.config/k9s-alpha/contexts` and contains the following files:

| File               |  Description                                                  |
| :----------------- | :------------------------------------------------------------ |
| benchmarks.yaml    | Defines custom benchmarking settings                          |
| config.yaml        | Defines a cluster specific configuration                      |
| scans.yaml         | Specifies the cluster scan excludes configurations            |
| skins.yaml         | Defines skins specific to that cluster                        |
| workloads.yaml     | Defines this cluster workload configurations                  |

For more details about each of these configurations, please see their individual specification in the Configuration section.

<br/>
<div class="note">
  <i class="fas fa-skull"></i> This is still in flux and will change while in pre-release stage!
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> The Main Configuration

K9s𝞪 keeps its main configurations under `$HOME/.config/k9s-alpha/config.yaml`.

```yaml
# $HOME/.config/k9s-alpha/config.yaml
k9s:
  # Sets the refreshRate for updating cluster resources. Default is 2 seconds
  refreshRate: 2
  # NEW! Sets the maximum number of retries when trying to connect to k8s api server.
  maxConnRetry: 5
  # NEW! Enable idiot light to warn the user for potentially destructive operations. Default is true
  # This options can be overridden in the Kubernetes context specific config file.
  idiotLight: true
  # Toggles mouse events
  enableMouse: false
  # Toggles header display.
  headless: false
  # Toggles crumbs.
  crumbsless: false
  # Treats the cluster as a read only cluster and turns off an editing functionality. Default is false
  # This option can also be overridden using either a command line option on in a context specific config.
  readOnly: true
  # Toggles terminal icons.
  noIcons: false
  # Define logger configuration.
  logger:
    # Tails the last xxx lines from the logs. Defaults 100.
    tail: 100
    # Sets the max number of lines to display while in log view. Defaults 5k.
    buffer: 5000
    # Set the timeline to retrieve the logs in seconds. Defaults 60secs.
    sinceSeconds: 60
    # Toggles log full screen display. Defaults false.
    fullScreenLogs: false
    # Toggles log text wrap. Defaults false.
    textWrap: false
    # Toggles show log time stamps. Default false.
    showTime: false
  # Sets thresholds for over cpu/memory alerts
  thresholds:
    # Sets cpu max thresholds. K9s𝞪will display an alert when these thresholds are exceeded.
    cpu:
      critical: 90
      warn: 70
    # Sets mem max thresholds. K9s𝞪will display an alert when these thresholds are exceeded.
    memory:
      critical: 90
      warn: 70
```