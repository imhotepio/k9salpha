---
layout: section
---

<i class="icon fas fa-hdd fa-7x"></i>

<br/>
<br/>
<br/>

# Contexts Configuration

New! In K9s𝞪 contexts now live in a separate directory structure namely `$HOME/.k9s-alpha/contexts`. Each contexts in your Kubernetes clusters can be configured differently. The tool will look at the presence of this context configuration and will use sensible defaults when not present.

There are currently two available context configuration namely feature gates and portforwards. More will come soon!

By enabling the nodeShell feature gate on a given context, K9s𝞪 allows you to shell into your cluster nodes. Once enabled, you will have a new mnemonic aka `s` for `shell` while in node view. K9s𝞪 will launch a pod on the selected node using a special k9s_shell pod. Furthermore, you can refine your shell pod by using a custom docker image preloaded with the shell tools you love. By default K9s𝞪 uses a BusyBox image, but you can configure it as follows:

<br/>
<div class="note">
  <i class="fas fa-skull"></i> Work in progress... Options and layout may change in future K9s𝞪 releases as this feature solidifies.
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Example

Enabling a node shell on context `blee`

```yaml
# $HOME/.k9s-alpha/context/blee/config.yml
k9s:
  cluster:
    featureGates:
      # You must enable the nodeShell feature gate to enable shelling into nodes.
      nodeShell: true
    # You can also further tune the shell pod specification by specify an image, namespace and resource limits.
    shellPod:
      image: cool_kid_admin:42
      namespace: blee
      limits:
        cpu: 100m
        memory: 100Mi
    # Define the portforward local address via ip or dns. Defaults to localhost.
    portForwardAddress: localhost
```
