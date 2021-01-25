---
layout: section
---

<i class="icon fas fa-hdd fa-7x"></i>

<br/>
<br/>
<br/>

# NodeShell

<br/>

## <img src="/assets/sections/overview.png" width="auto" height="32"/> Overview

By enabling the nodeShell feature gate on a given cluster, K9s allows you to shell into your cluster nodes. Once enabled, you will have a new `s` for `shell` menu option while in node view. K9s will launch a pod on the selected node using a special k9s_shell pod. Furthermore, you can refine your shell pod by using a custom docker image preloaded with the shell tools you love. By default k9s uses a BusyBox image, but you can configure it as follows:

<br/>
<div class="note">
  <i class="fas fa-skull"></i> Work in progress... Options and layout may change in future K9s releases as this feature solidifies.
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Example

Enabling a node shell on cluster `blee`

```yaml
# $HOME/.k9s/config.yml
k9s:
  clusters:
    # Configures node shell on cluster blee
    blee:
      featureGates:
        # You must enable the nodeShell feature gate to enable shelling into nodes
        nodeShell: true
      # You can also further tune the shell pod specification
      shellPod:
        image: cool_kid_admin:42
        namespace: blee
        limits:
          cpu: 100m
          memory: 100Mi
```
