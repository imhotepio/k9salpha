---
layout: section
---

<i class="icon fab fa-hotjar fa-7x"></i>

<br/>
<br/>
<br/>

# HotKeys

<br/>

## <img src="/assets/sections/overview.png" width="auto" height="32"/> Overview

Entering the command mode and typing a resource name or alias could be cumbersome for navigating thru often visited resources. By leveraging `hotkeys`, K9s can be configured to quickly navigate to your favorite resources. In order to enable hotkeys please follow these steps:

1. Create a file named `$HOME/.k9s/hotkey.yml`
2. Add the following to your `hotkey.yml`. You can use resource name/short name to specify a command ie same as typing it while in command mode.

Not feeling so hot? Your custom hotkeys will be listed in the help view `?`. Also your hotkey file will be automatically reloaded so you can readily use your hotkeys as you define them.

You can choose any keyboard shortcuts that make sense to you, provided they are not part of the standard K9s shortcuts list.

<br/>
<div class="note">
  <i class="fas fa-skull"></i> This configuration might change in future releases!
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Example

```yaml
# $HOME/.k9s/hotkey.yml
hotKey:

  # Hitting Shift-0 navigates to your pod view
  shift-0:
    shortCut:    Shift-0
    description: Viewing pods
    command:     pods

  # Hitting Shift-1 navigates to your deployments
  shift-1:
    shortCut:    Shift-1
    description: View deployments
    command:     dp

  # Hitting Shift-2 navigates to your xray deployments
  shift-2:
    shortCut:    Shift-2
    description: XRay Deployments
    command:     xray deploy
```
