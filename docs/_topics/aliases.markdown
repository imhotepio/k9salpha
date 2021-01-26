---
layout: section
---

[<img src="/assets/sections/dragon_1.png" align="right" width="200" height="auto"/>](/)

<br/>
<br/>
<br/>

# Aliases

In K9s𝞪 you can define your very own command aliases (short-names) to access your resources. In your `$HOME/.k9s-alpha` define a file called `alias.yml`. A K9s𝞪 alias is defined via a pairs of the form alias-name:GVR. A GVR (Group/Version/Resource) represents a fully qualified Kubernetes resource identifier using the plural name form of a resource ie group/version/resource name.

<br/>

### <img src="/assets/sections/examples.png" width="auto" height="32"/> Example

Using this alias file, you can now type pp/crb to list pods or ClusterRoleBindings respectively.

```yaml
# $HOME/.k9s-alpha/alias.yml
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

<br/>

## <img src="/assets/sections/overview.png" width="auto" height="32"/> AutoSuggest

<br/>
K9s𝞪 command mode supports autosuggestions. Suggestions are based on supported Kubernetes resource in singular/plural as well as short names and command aliases as describe below. The command mode supports the following keys:

| Key                | Description                              |
| ------------------ | ---------------------------------------- |
| ⬆️ ⬇️                | Navigate up or down thru the suggestions |
| `Ctrl-w`, `Ctrl-u` | Clear out the command                    |
| `Tab`, `Ctrl-f`, ➡️ | Accept the suggestion                    |
