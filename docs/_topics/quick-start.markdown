---
layout: section
---

<i class="icon fas fa-terminal fa-7x"></i>

<br/>
<br/>
<br/>

<br/>

## <img src="/assets/sections/overview.png" width="auto" height="32"/> CLI

K9s𝞪 CLI comes with a few options to launch the tool with different configurations.

```shell
# List all available CLI options
k9salpha help

# Get info about K9s𝞪 runtime (logs, configs, etc..)
k9salpha info

# Run K9s𝞪 in a given namespace.
k9salpha -n mycoolns

# Run K9s𝞪 and launch in pod view via the pod command.
k9salpha -c pod

# Start K9s𝞪 in a using a specific KubeConfig context
k9salpha --context coolCtx

# Start K9s𝞪 in readonly mode - with all modification commands disabled
k9salpha --readonly

# Start K9s𝞪 in debug mode. See logs location using the k9salpha info command above
k9salpha -l debug
```

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Artifact Locations

K9sAlpha now uses [XDG](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html) to store its various configurations, data, logs, etc... The table below defines the various env variable you can define and the default locations. Please see the refer to the XDG spec for more details on overriding this locations.

| Env Vars        | Unix                                | MacOS                           | Windows                |
| :-------------- | :---------------------------------- | :------------------------------ | :--------------------- |
| XDG_CONFIG_HOME | `~/.config`                         | `~/Library/Preferences`         | `%LOCALAPPDATA%`       |
| XDG_DATA_HOME   | `~/.local/share`                    | `~/Library/Application Support` | `%LOCALAPPDATA%`       |
| XDG_CACHE_HOME  | `~/.cache`                          | `~/Library/Caches`              | `%LOCALAPPDATA%\cache` |
| XDG_STATE_HOME  | `~/.local/state`                    | `~/Library/Application Support` | `%LOCALAPPDATA%\state` |

K9sAlpha artifacts are stored in the locations above under the `k9s-alpha` directory.

| Env var         | K9s Artifacts | Description                    |
| :-------------- | :------------ | :----------------------------- |
| XDG_CONFIG_HOME | config.yaml   | General configuration          |
| XDG_DATA_HOME   | contexts      | K8s contexts configurations    |
| XDG_CACHE_HOME  | config.yaml   | active contexts, views, ns     |
| XDG_STATE_HOME  | config.yaml   | logs, screen-dumps, benchmarks |