---
layout: section
---

<i class="icon fas fa-hdd fa-7x"></i>

<br/>
<br/>
<br/>

# Workloads

You can now tell K9s to monitor your various workloads by defining a `workload.yml` file for a given Kubernetes context.
Given a set of labels, Alpha will monitor all ressources associated with those labels and present the results in a workloads view.
You can access the view by using either `workloads` or the shortcut `wk`. This is the equivalent to using `kubectl get all -lapp=fred` with a twist as workloads will go deeper into your matching resources in good all k9s style!

When a workload is specified, K9sAlpha will scan the associated resources and report any potential issues with their configuration. These are referred as resource `scans` in K9sAlpha parlance. The tool will classify scans as severe, warning or info and will give detailed reports on these scans and which resources are affected.
Please refer to the scan section for additional information.

IMPORTANT! The scans are not quiet on par with Popeye's sanitizers! We will refine and beef-up in upcoming releases!

Additionally, you have the option to tell k9s where the resources manifests are located on disk. In these situations, the tool will perform resource diffs and report the deltas between the `source of truth` aka the manifests on disk and what's currently deployed on the cluster. When deltas are detected, K9sAlpha will produce detailed reports of the differences via `Deltas`.

IMPORTANT! Alpha currently only support plain old k8s manifests or Kustomizations to compute the deltas.

NOTE! These queries are highly process/mem intensive and mileage will vary depending on the clusters size and resources complexity!

<br/>
<div class="note">
  <i class="fas fa-skull"></i> Work in progress... Options and layout may change in future K9s𝞪 releases as this feature solidifies.
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Sample Workloads

```yaml
workloads:
  # Define a workload named blee.
  blee:
    # Specify labels for all resources you want to track for this workload.
    labels:
      app: blee
      env: prod
      group: blee
    # Specify either a single manifest file or a directory. A single manifest file may contain multiple resource definitions.
    # IMPORTANT! Currently we only support plain K8s manifests or Kustomizations.
    manifests: /k8s/manifests/blee.yml
  zorg:
    labels:
      app: zorg
      org: cover-the-world-with-red-hot-magma
    manifests: /k8s/manifests/zorg
```
