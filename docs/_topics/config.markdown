---
layout: section
---

<i class="fas fa-cogs icon fa-7x"></i>

<br/>
<br/>
<br/>

# Configuration

<br/>

## <img src="/assets/sections/overview.png" width="auto" height="32"/> Application Configuration

K9s𝞪 keeps its configurations in your home directory dotfile under `$HOME/.k9s-alpha`.
The main configuration file is named `config.yml` and stores various K9s𝞪 specific bits.

<br/>
<div class="note">
  <i class="fas fa-skull"></i> This is still in flux and will change while in pre-release stage!
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Main Configuration

There is a departure here from the original K9s. Context specific configurations now resides in a new directory location aka `contexts`.

```yaml
# $HOME/.k9s-alpha/config.yml
k9s:
  # Sets the refreshRate for updating cluster resources.
  refreshRate: 2
  # NEW! Sets the default dump directory when saving resources.
  dumpDir: /tmp/k9s
  # NEW! Sets the maximum number of retries when connecting to k8s api server.
  maxConnRetry: 5
  # Toggles mouse events
  enableMouse: false
  # Toggles header display.
  headless: false
  # Toggles crumbs.
  crumbsless: false
  # Sets whether or not K9s𝞪should be able to alter cluster resources.
  readOnly: false
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

<br/>

## <img src="/assets/sections/overview.png" width="auto" height="32"/> Kubernetes Contexts Configuration

K9s𝞪 keeps available Kubernetes contexts configurations under `$HOME/.k9s-alpha/contexts`. Each Kubernetes contexts have multiple configurations that can further refine the tool. Things like feature gates, skins, scans, workloads and benchmarking options are all configurations set at the context level.

For a given Kubernetes context, K9s𝞪 expects the following directory organization and structure under `$HOME/.k9s-alpha`:

```text
contexts
  contextA
    benchmarks.yml
    config.yml
    scans.yml
    skins.yml
    workloads.yml
  contextB
    benchmarks.yml
    config.yml
    scans.yml
    skins.yml
    workloads.yml
```

If these files do not exist on disk, K9s𝞪 will take a default stance for each separate configurations where applicable.
For more details about each of these configurations, please see their individual specification in the help section.

<br/>
<div class="note">
  <i class="fas fa-skull"></i> This is still in flux and will change while in pre-release stage!
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Sample Cluster Config

Define a specific cluster configuration in the given context.

```yaml
# $HOME/.k9s-alpha/contexts/contextA/config.yml
k9s:
  cluster:
    featureGates:
      nodeShell: true
    shellPod:
      image: busybox:1.31
      namespace: default
      limits:
        cpu: 100m
        memory: 100Mi
    portForwardAddress: localhost
```

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Sample Benchmark Config

Specifies `hey` benchmarking configuration for pods and services.

```yaml
# $HOME/.k9s-alpha/contexts/contextA/benchmarks.yml
benchmarks:
  defaults:
    concurrency: 2
    requests: 500
  containers:
    default/nginx:nginx:
      concurrency: 2
      requests: 2000
      http:
        method: GET
        path: /
```

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Sample Scans Config

Specifies which particular resources and codes should be excluded from the cluster scans.

```yaml
# $HOME/.k9s-alpha/contexts/contextA/scans.yml
k9s:
  bans:
    globals:
      sidecars:
        - istio-proxy
      codes:
        - CON-04
    gvrs:
      v1/namespaces:
        rx:kube:
      v1/pods:
        default/nginx-sts-0:
          codes:
            - CON-03
            - CON-06
      v1/secrets:
        default/sc1:
        default/sc2:
      v1/services:
        default/nginx:
          codes:
            - SVC-04
```

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Sample Skins Config

Defines a specific skin configuration for a given context for your eye balls delight. Additionaly, this can provide an extra visual cues while managing multiple contexts.
Please see the skins directory in this  repo for template ideas.

```yaml
# $HOME/.k9s-alpha/contexts/contextA/skins.yml
k9s:
  # General K9s𝞪styles
  body:
    fgColor: *foreground
    bgColor: *background
    logoColor: *magenta
  # ClusterInfoView styles.
  info:
    fgColor: *pink
    sectionColor: *foreground
  ...
```

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Sample Workloads Config

Workloads provide for categorizing related cluster resources by using labels to query cluster resources.

```yaml
# $HOME/.k9s-alpha/contexts/contextA/workloads.yml
workloads:
  nginx:
    labels:
      app: nginx
      env: prod
      fred: blee
    manifests: /Users/fernand/work/myprojects/K9sAlpha/k9s/k8s/nginx-dir/nginx.yml
  sts:
    labels:
      app: nginx-sts
    manifests: /Users/fernand/work/myprojects/K9sAlpha/k9s/k8s/nginx-sts-dir
  zoro:
    labels:
      app: bumble-bee-tuna
```
