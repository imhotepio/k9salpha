---
layout: section
---

<i class="icon fas fa-hdd fa-7x"></i>

<br/>
<br/>
<br/>

# Scans

New! In K9s𝞪 when workloads are detected, resources associated with the workload will be scans to report potential issues or anomalies. Although, we always recommend wide open scans to avoid potential hidden issues, one may want to exclude certain resources from the scans are they may not be either pertinent to the workload or may come from other subsystems. For example , you may have valid arguments for not specifying probes or not wanting to report on istio sidecars. For this reason, you can further qualify scans exclusions in a context specific file `$HOME/,k9salpha/contexts/contextA/scans.yml`.

<div class="center">
  <img src="/assets/screens/radars.png" align="center" width="800" height="auto">
  <br/>
  K9s𝞪 Radar View
</div>

<br/>
<div class="note">
  <i class="fas fa-skull"></i> Work in progress... Options and layout may change in future K9s𝞪 releases as this feature solidifies.
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Example

```yaml
# $HOME/.k9s-alpha/contexts/blee/scans.yml
k9s:
  bans:
    # Global bans will apply to all scannable resources and codes
    globals:
      # Exclude the following sidecar containers from the scans.
      sidecars:
        - istio-proxy
      # Exclude to following codes from the scans.
      codes:
        # Ignore all reports about missing docker container image tag.
        - CON-04
    # GVRS express resource level exclusions. GVR=Group/Version/Pluralize-Resource-Name
    gvrs:
      # Exclude certain namespaces from the scans
      v1/namespaces:
        # Exclude resources in the fred namespace.
        fred:
        # Exclude all namespaces matching the regular expression. ie kube-system, kube-public, kube-node-lease
        # NOTE! rx: here specifies a valid regular expression is given.
        rx:kube:
      # Exclude certain pods from the scans.
      v1/pods:
        # Exclude StatefulSet pod nginx-sts-1 in the default namespace.
        # The shape matches an FQN=Fully Qualified Resource Name ie namespace-name/resource-name
        default/nginx-sts-1:
          codes:
            - CON-04
            - CON-06
      # Exclude certain secrets from the scans.
      v1/secrets:
        # Exclude sc1 in namespace default
        default/sc1:
      # Exclude certain codes from the following services.
      v1/services:
        # Exclude code SVC-04 (prefer port name vs number)
        default/nginx:
          codes:
            - SVC-04
```
