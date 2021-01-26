---
layout: section
---

<i class="icon fab fa-hotjar fa-7x"></i>

<br/>
<br/>
<br/>

# HotKeys

Entering the command mode and typing a resource name or alias could be cumbersome for navigating thru often visited resources. By leveraging `hotkeys`, K9s𝞪 can be configured to quickly navigate to your favorite resources. In order to enable hotkeys create a file `$HOME/.k9s-alpha/hotkey.yml`

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Example

<br/>
<div class="note">
  <i class="fas fa-skull"></i> This configuration might change in future releases!
</div>

<br/>

```yaml
# $HOME/.k9s-alpha/hotkey.yml
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
    description: XRay Deployments
    command:     xray deploy
```

<br/>
---

## <img src="/assets/sections/overview.png" width="auto" height="32"/> Not feeling so hot?

You can list all your active hot-key using the help view `?`. To boot, your hotkey file will be automatically reloaded so you can readily use your hotkeys as you define them.

NOTE! You can choose any keyboard shortcuts that make sense to you, provided they are not already registered as a standard K9s𝞪 mnemonic.
