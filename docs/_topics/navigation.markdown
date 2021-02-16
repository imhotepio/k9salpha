---
layout: section
---

<i class="icon far fa-compass fa-7x"></i>

<br/>
<br/>
<br/>

<br/>

## <img src="/assets/sections/overview.png" width="auto" height="32"/> Navigation

Below is a short list of K9s𝜶 survival commands. For more command key bindings please use `?` key while in the application.

| Action                                                         | Example                       | Description                                                            |
|----------------------------------------------------------------|-------------------------------|------------------------------------------------------------------------|
| Help                                                           | `?`                           | Display context sensitive help                                         |
| Aliases                                                        | `ctrl-a`                      | List available cluster resources and aliases                           |
| Exit                                                           | `:q`, `ctrl-c`                | Terminates the application                                             |
| Bails out of view/command/filter mode                          | `<esc>`                       |                                                                        |
| View a resource                                                | `:pod`                        | Accepts singular, plural, short-name or alias<br/> ie `:po`,`:pod`,`:pods` to list pods |
| View a resource in a namespace                                 | `:pod default`                |                                                                        |
| Filter out a resource view given a filter                      | `/fred`                       | Regex2 supported ie `fred|blee` to filter resources named fred or blee |
| Inverse regex filer                                            | `/! fred`                     | Keep everything that *doesn't* match.                                  |
| Filter resource by labels                                      | `/-l app=fred⏎`               | filter pods with labels app=fred                                       |
| Fuzzy find a resource given a filter                           | `/-f frd`                     |                                                                        |
| Key mapping to describe, view, edit, view logs,...             | `d`,`v`, `e`, `l`,...         |                                                                        |
| List all available Contexts                                    | `:ctx⏎`                       | List all available from kubeconfig or env var                          |
| Navigate to a given context                                    | `:ctx context-name⏎`          | Switch to fred context `:ctx fred`                                     |
| List all available namespaces                                  | `:ns⏎`                        |                                                                        |
| To view all saved resources                                    | `:screendump` or `sd⏎`        | View all screen dump                                                   |
| To delete a resource                                           | `ctrl-d`                      | Dialog pops up to confirm (use TAB/SHIFT-TAB,ENTER to navigate fields  |
| Force delete a resource                                        | `ctrl-k`                      | WARN! Power users ie No confirmation dialog                            |
