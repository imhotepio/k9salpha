---
layout: section
---

<i class="icon fas fa-key fa-7x"></i>

<br/>
<br/>
<br/>

# RBAC

On RBAC enabled clusters, cluster admins will need to give your users/groups enough capabilities for them to explore their cluster. At the very least, K9s𝞪 needs get/list/watch privileges at both the cluster and namespace level to display resources and metrics.

These rules below are just suggestions. You will need to customize them based on your environment policies. If you need to edit/delete resources extra Fu will be necessary.

<div class="center">
  <img src="/assets/screens/rbac.png" align="center" width="800" height="auto">
  <br/>
  K9s𝞪 RBAC View
</div>

<br/>
<div class="note">
  <i class="fas fa-skull"></i> Cluster/Namespace access may change in the future as K9s𝞪evolves.
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> ClusterRole

```yaml
---
# K9s𝞪Reader ClusterRole
kind: ClusterRole
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: k9s
rules:
  # Grants RO access to cluster resources node and namespace
  - apiGroups: [""]
    resources: ["nodes", "namespaces", "persistentvolumes"]
    verbs: ["get", "list", "watch"]
  # Grants RO access to RBAC resources
  - apiGroups: ["rbac.authorization.k8s.io"]
    resources: ["clusterroles", "roles", "clusterrolebindings", "rolebindings"]
    verbs: ["get", "list", "watch"]
  # Grants RO access to CRD resources
  - apiGroups: ["apiextensions.k8s.io"]
    resources: ["customresourcedefinitions"]
    verbs: ["get", "list", "watch"]
  # Grants RO access to metric server (if present)
  - apiGroups: ["metrics.k8s.io"]
    resources: ["nodes", "pods"]
    verbs: ["get", "list", "watch"]

---
# Sample K9s𝞪user ClusterRoleBinding
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: k9s
subjects:
  - kind: User
    name: fernand
    apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: k9s
  apiGroup: rbac.authorization.k8s.io
```

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Role

If your users are constrained to certain namespaces, K9s𝞪 will need to following role to enable read access to namespaced resources.

```yaml
---
# K9s𝞪Reader Role (default namespace)
kind: Role
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: k9s
  namespace: default
rules:
  # Grants RO access to most namespaced resources
  - apiGroups: ["", "apps", "autoscaling", "batch", "extensions"]
    resources: ["*"]
    verbs: ["get", "list", "watch"]
  # Grants RO access to metric server
  - apiGroups: ["metrics.k8s.io"]
    resources: ["pods", "nodes"]
    verbs:
      - get
      - list
      - watch

---
# Sample K9s𝞪 user RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: k9s
  namespace: default
subjects:
  - kind: User
    name: fernand
    apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: k9s
  apiGroup: rbac.authorization.k8s.io
```
