---
layout: section
---

<i class="icon fas fa-hdd fa-7x"></i>

<br/>
<br/>
<br/>

# Contexts Configuration

New! In K9s𝞪 contexts now live in a separate directory structure namely `$HOME/.config/k9s-alpha/contexts`. Each contexts in your Kubernetes clusters can be configured differently. The tool will look at the presence of this context specific directory or will use sensible defaults when not present.

Context specific configurations have several functions:

1. Override general configurations when the context is active such as read access, idiot light, enabling feature gates, etc..
1. Specify cluster specific benchmarking profile and skins
1. Define cluster workloads and cluster scans exclusions

<br/>
<div class="note">
  <i class="fas fa-skull"></i> Work in progress... Options and layout may change in future K9s𝞪 releases as this feature solidifies.
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Example

By enabling the nodeShell feature gate on a given context, K9s𝞪 allows you to shell into your cluster nodes. Once enabled, you will have a new mnemonic aka `s` for `shell` while in node view. K9s𝞪 will launch a pod on the selected node using a special k9s_shell pod. Furthermore, you can refine your shell pod by using a custom docker image preloaded with the shell tools you love. By default K9s𝞪 will use a BusyBox image, but you can override it.

Enabling a node shell on context `blee`

```yaml
# $HOME/.config/k9s-alpha/contexts/blee/config.yaml
k9s:
  cluster:
    # Overrides default readOnly mode on this context
    readOnly: false
    # Overrides idiot light
    idiotLight: true
    featureGates:
      # You must enable the nodeShell feature gate to enable shelling into nodes.
      nodeShell: true
    # You can also further tune the shell pod specification by specify an image, namespace and resource limits.
    shellPod:
      image: cool-kids-admin-tools:v4.2
      namespace: admin-tools
      limits:
        cpu: 100m
        memory: 100Mi
    # Define the portforward local address via IP or DNS. Default localhost.
    portForwardAddress: localhost
```
