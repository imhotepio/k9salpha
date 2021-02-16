---
layout: section
---

<i class="icon fas fa-plug fa-7x"></i>

<br/>
<br/>
<br/>

# Plugins

K9s𝞪 allows you to extend your command line and tooling by defining your very own cluster commands via plugins. Plugins are defined a file named `$HOME/.config/k9s-alpha/plugins.yaml`.

A plugin is defined as follows:

* Shortcut option represents the key combination a user would type to activate the plugin
* Description will be printed next to the shortcut in the K9s𝞪 menu
* Scopes defines a collection of resources name/short-name for the views associated with the plugin. You can specify `all` to provide this shortcut for all views.
* Command represents ad-hoc commands the plugin runs upon activation
* Background specifies whether or not the command runs in the background
* Args specifies the various arguments that should apply to the command above

K9s𝞪 does provide additional environment variables for you to customize your plugins arguments. Currently, the available environment variables are as follows:

* `$NAMESPACE` -- the current active namespace
* `$NAME` -- the selected resource name
* `$CONTAINER` -- the current container if any
* `$FILTER` -- the current filter if any
* `$KUBECONFIG` -- the KubeConfig location.
* `$CLUSTER` the active cluster name
* `$CONTEXT` the active context name
* `$USER` the active user
* `$GROUPS` the active groups
* `$POD` while in a container view
* `$COL-<RESOURCE_COLUMN_NAME>` use a given column name for a viewed resource.

For inspiration, please take a look at some of the [K9s𝞪 Community Plugins](https://github.com/imhotepio/k9salpha/tree/master/plugins) contributed by our K9sers friends.

<br/>
<div class="note">
  <i class="fas fa-skull"></i> Work in progress... Options and layout may change in future K9s𝞪 releases as this feature solidifies.
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Example

This defines a plugin for viewing logs on a selected pod using `ctrl-l` mnemonic.

```yaml
# $HOME/.config/k9s-alpha/plugins.yaml
plugins:
  # Defines a plugin named fred to provide a `ctrl-l` shortcut to tail the logs while in pod view.
  view-logs:
    # Define a mnemonic to invoke the plugin
    shortCut: Ctrl-L
    # What will be shown on the K9s𝞪menu
    description: Pod logs
    # Collections of views that support this shortcut. (You can use `all`)
    scopes:
    - po
    # The command to run upon invocation. Can use Krew plugins here too!
    command: kubectl
    # Presents a confirmation dialog prior to proceeding
    config: true
    # Whether or not to run the command in background mode
    background: false
    # Defines the command arguments
    args:
    - logs
    - -f
    - $NAME
    - -n
    - $NAMESPACE
    - --context
    - $CONTEXT
```
