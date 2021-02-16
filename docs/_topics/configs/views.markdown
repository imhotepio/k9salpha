---
layout: section
---

<i class="icon fas fa-columns fa-7x"></i>

<br/>
<br/>
<br/>

# Views

[SneakCast v0.17.0 on The Beach! - Yup... Sound is sucking but what a setting!](https://youtu.be/7S33CNLAofk)

K9s𝞪 provides for customizing your resource columns while in table views. You can configure which column and columns order to use when displaying a given Kubernetes resource.

To surface this feature, you will need to create a new configuration file, namely `$HOME/.config/k9s-alpha/views.yaml`. This file leverages GVR (Group/Version/Resource) to configure the associated table view columns. If no GVR is found for a view the default rendering will take over (ie what you have now). Going wide `Ctrk-W` will add all the remaining columns that are available on the given resource after your custom columns. To boot, you can edit your views config file live and tune your resources views to your liking!

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Example

Here is a sample views configuration that customize a pods and services views.

```yaml
# $HOME/.config/k9s-alpha/views.yaml
k9s:
  views:
    # Alters the pod view column layout. Uses GVR as key
    v1/pods:
      columns:
        - AGE
        - NAMESPACE
        - NAME
        - IP
        - NODE
        - STATUS
        - READY
    # Alters the service view column layout
    v1/services:
      columns:
        - AGE
        - NAMESPACE
        - NAME
        - TYPE
        - CLUSTER-IP
```
