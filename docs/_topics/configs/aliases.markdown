---
layout: section
---

[<img src="/assets/sections/dragon_1.png" align="right" width="200" height="auto"/>](/)

<br/>
<br/>
<br/>

# Aliases

In K9s𝞪 you can define your very own command aliases (short-names) to access your favorite Kubernetes resources. Custom aliases reside in a file called `$HOME/.config/k9s-alpha/aliases.yaml`. A K9s𝞪 alias is defined via a pair `alias-name`:`GVR`. A GVR (Group/Version/Resource) represents a fully qualified Kubernetes resource identifier using the plural form of a resource name.

<br/>

### <img src="/assets/sections/examples.png" width="auto" height="32"/> Example

Using this alias file, you can now type pp/crb to list pods or ClusterRoleBindings respectively.

```yaml
# $HOME/.config/k9s-alpha/aliases.yaml
alias:
  # Use pp as an alias for Pod
  pp: v1/pods

  # Use crb as an alias for ClusterRoleBinding
  crb: rbac.authorization.k8s.io/v1/clusterrolebindings

  # Use cr as an alias for ClusterRole
  cr: rbac.authorization.k8s.io/v1/clusterroles

  # Use dep as an alias for Deployments
  dep: apps/v1/deployments

  # Use fred as an alias for CRD Frederick
  fred: acme.io/v1alpha1/fredericks
```
