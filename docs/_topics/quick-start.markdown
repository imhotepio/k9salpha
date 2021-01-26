---
layout: section
---

<i class="icon fas fa-terminal fa-7x"></i>

<br/>
<br/>
<br/>

<br/>

## <img src="/assets/sections/overview.png" width="auto" height="32"/> CLI

K9s𝞪 CLI comes with a view options to launch the tool with different configurations.

```shell
# List all available CLI options
k9salpha help

# Get info about K9s𝞪 runtime (logs, configs, etc..)
k9salpha info

# Run K9s𝞪 in a given namespace.
k9salpha -n mycoolns

# Run K9s𝞪 and launch in pod view via the pod command.
k9salpha -c pod

# Start K9s𝞪 in a non default KubeConfig context
k9salpha --context coolCtx

# Start K9s𝞪 in readonly mode - with all modification commands disabled
k9salpha --readonly
```

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> In App KeyBoard Bindings

| Action                                                         | Example                       | Description                                                            |
|----------------------------------------------------------------|-------------------------------|------------------------------------------------------------------------|
| Help                                                           | `?`                           | Display context sensitive help                                         |
| Aliases                                                        | `ctrl-a`                      | List available cluster resources and aliases                           |
| Exit                                                           | `:q`, `ctrl-c`                | Terminates the application                                             |
| View a resource                                                | `:resource⏎`                  | Accepts singular, plural, short-name or  alias ie `:po`,`:pod`,`:pods` to list pods |
| Navigate to a resource in a given namespace                    | `:resourcce namespace⏎`       | List pods in namespace kube-system `:po kube-system`                   |
| Filter out a resource view given a filter                      | `/filter⏎`                    | Regex2 supported ie `fred|blee` to filter resources named fred or blee |
| Inverse regex filer                                            | `/! filter⏎`                  | Keep everything that *doesn't* match.                                  |
| Filter resource by labels                                      | `/-l app=fred⏎`               | filter pods with labels app=fred                                       |
| Fuzzy find a resource given a filter                           | `/-f filter⏎`                 |                                                                        |
| Bails out of view/command/filter mode                          | `<esc>`                       |                                                                        |
| Key mapping to describe, view, edit, view logs,...             | `d`,`v`, `e`, `l`,...         |                                                                        |
| List K8s Contexts                                              | `:ctx⏎`                       | List all available from kubeconfig or env var                          |
| Navigate to a given context                                    | `:ctx context-name⏎`          | Switch to fred context `:ctx fred`                                     |
| List all K8s namespaces                                        | `:ns⏎`                        |                                                                        |
| To view all saved resources                                    | `:screendump` or `sd⏎`        | View all screen dump                                                   |
| To delete a resource                                           | `ctrl-d`                      | Dialog pops up to confirm (use TAB/SHIFT-TAB,ENTER to navigate fields  |
| Force delete a resource                                        | `ctrl-k`                      | NOTE: Power users - No confirmation dialog                             |
