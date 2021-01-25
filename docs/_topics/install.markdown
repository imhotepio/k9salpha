---
layout: section
---

<i class="icon fas fa-tools fa-7x"></i>

<br/>
<br/>
<br/>

# Installation

<br/>

---
## <img src="/assets/sections/overview.png" width="auto" height="32"/> Overview

K9s is available on Linux, macOS and Windows platforms.

* Binaries for Linux, Windows and Mac are available as tarballs in the [release](https://github.com/derailed/k9s/releases) page.

* MacOS

   ```shell
   # Via Homebrew
   brew install derailed/k9s/k9s
   # Via MacPort
   sudo port install k9s
   ```

* Linux

   ```shell
   # Via LinuxBrew
   brew install derailed/k9s/k9s
   # Via PacMan
   pacman -S k9s
   ```

* Windows

  ```shell
  # Via scoop
  scoop install k9s
  # Via chocolatey
  choco install k9s
  ```

## Building From Source

 K9s is currently using go v1.14 or above. In order to build K9 from source you must:

 1. Clone the repo
 2. Build and run the executable

      ```shell
      make build && ./execs/k9s
      ```

## PreFlight Check

* K9s uses 256 colors terminal mode. On `Nix system make sure TERM is set accordingly.

    ```shell
    export TERM=xterm-256color
    ```
