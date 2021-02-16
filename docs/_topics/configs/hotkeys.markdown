---
layout: section
---

<i class="icon fab fa-hotjar fa-7x"></i>

<br/>
<br/>
<br/>

# HotKeys

Entering the command mode and typing a resource name or alias could be cumbersome for navigating quickly thru often visited resources. For this purpose, you can define `hotkeys` to quickly access your resources. HotKeys are defined in a file `$HOME/.config/k9s-alpha/hotkeys.yaml` using the syntax presented below.

<br/>
<div class="note">
  <i class="fas fa-skull"></i> This configuration might change in future releases!
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Example

Defines hot keys for navigating pods, deployments, services using keys Shift-0, Shift-1, Shift-2 respectively.

<br/>

```yaml
# $HOME/.config/k9s-alpha/hotkeys.yaml
hotKey:

  # Shift-0 navigates to the pod view in the current namespace.
  shift-0:
    shortCut:    Shift-0
    description: Viewing pods
    command:     pods

  # Shift-1 navigates to the deployment view in namespace fred.
  shift-1:
    shortCut:    Shift-1
    description: View deployments
    command:     dp fred

  # Hitting Shift-2 navigates to the xray view.
  shift-2:
    shortCut:    Shift-2
    description: Services
    command:     services
```

<br/>
---

## <img src="/assets/sections/overview.png" width="auto" height="32"/> Not feeling so hot?

You can list all your active hot-key using the help view `?`. To boot, your hotkey file will be automatically reloaded so you can readily use your hotkeys as you define them.

NOTE! You can choose any keyboard shortcuts that make sense to you, provided they are not already registered as a standard K9s𝞪 mnemonic.
