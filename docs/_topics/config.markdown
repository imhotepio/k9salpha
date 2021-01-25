---
layout: section
---

<i class="fas fa-cogs icon fa-7x"></i>

<br/>
<br/>
<br/>

# Configuration

<br/>

## <img src="/assets/sections/overview.png" width="auto" height="32"/> Overview

K9s keeps its configurations in a .k9s directory in your home directory `$HOME/.k9s`. The main configuration file is named `config.yml` and stores various K9s specific bits. This file
will be updated by k9s to store current view and namespaces information.

<br/>
<div class="note">
  <i class="fas fa-skull"></i> This is still in flux and will change while in pre-release stage!
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> K9s CLI Configuration

```yaml
# $HOME/.k9s/config.yml
k9s:
  # Represents ui poll intervals. Default 2secs
  refreshRate: 2
  # Number of retries once the connection to the api-server is lost. Default 15.
  maxConnRetry: 5
  # Enable mouse support. Default false
  enableMouse: true
  # Set to true to hide K9s header. Default false
  headless: false
  # Set to true to hide K9s crumbs. Default false
  crumbsless: false
  # Indicates whether modification commands like delete/kill/edit are disabled. Default is false
  readOnly: false
  # Toggles icons display as not all terminal support these chars.
  noIcons: false

  # Logs configuration
  logger:
    # Defines the number of lines to return. Default 100
    tail: 200
    # Defines the total number of log lines to allow in the view. Default 1000
    buffer: 500
    # Represents how far to go back in the log timeline in seconds. Setting to -1 will show all available logs. Default is 5mins.
    sinceSeconds: 300
    # Go full screen while displaying logs. Default false
    fullScreenLogs: false
    # Toggles log line wrap. Default false
    textWrap: false
    # Toggles log line timestamp info. Default false
    showTime: false

  # Indicates the current Kube context. Defaults to current context
  currentContext: minikube
  # Indicates the current kube cluster. Defaults to current context cluster
  currentCluster: minikube
  # Persists per cluster preferences for favorite namespaces and view.

  clusters:
    cluster1:
      namespace:
        active: coolio
        favorites:
        - cassandra
        - default
      view:
        active: po
      featureGates:
        # Toggles NodeShell support. Allow K9s to shell into nodes if needed. Default false.
        nodeShell: false
      # Provide shell pod customization of feature gate is enabled
      shellPod:
        # The shell pod image to use.
        image: killerAdmin
        # The namespace to launch to shell pod into.
        namespace: fred
        # The resource limit to set on the shell pod.
        limits:
          cpu: 100m
          memory: 100Mi
      # The IP Address to use when launching a port-forward.
      portForwardAddress: 1.2.3.4
    cluster2:
      namespace:
        active: all
        favorites:
        - all
        - kube-system
        - default
      view:
        active: dp
```
