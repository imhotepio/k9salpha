---
layout: section
---

<i class="icon fas fa-tachometer-alt fa-7x"></i>

<br/>
<br/>
<br/>

# Benchmarking

<br/>

## <img src="/assets/sections/overview.png" width="auto" height="32"/> Overview

K9s integrates [Hey](https://github.com/rakyll/hey) from the brilliant and super talented [Jaana Dogan](https://github.com/rakyll). `Hey` is a CLI tool to benchmark HTTP endpoints similar to AB bench. This preliminary feature currently supports benchmarking port-forwards and services (Read the paint on this is way fresh!).

To setup a port-forward, you will need to navigate to the PodView, select a pod and a container that exposes a given port. Using `SHIFT-F` a dialog comes up to allow you to specify a local port to forward to. Once acknowledged, you can navigate to the PortForward view (alias `pf`) listing out your active port-forwards. Selecting a port-forward and using `CTRL-B` will run a benchmark on that HTTP endpoint. To view the results of your benchmark runs, go to the Benchmarks view (alias `be`). You should now be able to select a benchmark and view the run stats details by pressing `<ENTER>`. NOTE: Port-forwards only last for the duration of the K9s session and will be terminated upon exit.

Initially, the benchmarks will run with the following defaults:

* Concurrency Level: 1
* Number of Requests: 200
* HTTP Verb: GET
* Path: /

The PortForward view is backed by a new K9s config file namely: `$HOME/.k9s/bench-<my_context>.yml`. Each cluster you connect to will have its own bench config file. Changes to this file should automatically update the PortForward view to indicate how you want to run your benchmarks.

<br/>
<div class="note">
  <i class="fas fa-skull"></i> Please keep in mind this file will likely change in subsequent releases!
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Example

```yaml
# $HOME/.k9s/bench-<my_k8s_context>.yml
benchmarks:
  # Indicates the default concurrency and number of requests setting if a container or service rule does not match.
  defaults:
    # One concurrent connection
    concurrency: 2
    # Number of requests that will be sent to an endpoint
    requests: 1000
  containers:
    # Containers section allows you to configure your http container's endpoints and benchmarking settings.
    # NOTE: the container ID syntax uses namespace/pod-name:container-name
    default/nginx:nginx:
      # Benchmark a container named nginx using POST HTTP verb using http://localhost:port/bozo URL and headers.
      concurrency: 1
      requests: 10000
      http:
        path: /bozo
        method: POST
        body:
          {"fred":"blee"}
        header:
          Accept:
            - text/html
          Content-Type:
            - application/json
  services:
    # Similarly you can Benchmark an HTTP service exposed either via NodePort, LoadBalancer types.
    # Service ID is ns/svc-name
    default/nginx:
      # Set the concurrency level
      concurrency: 5
      # Number of requests to be sent
      requests: 500
      http:
        method: GET
        # This setting will depend on whether service is ModePort or LoadBalancer. NodePort may require vendor port tunneling setting.
        # Set this to a node if ModePort or LB if applicable. IP or dns name.
        host: 1.2.3.4
        path: /bumblebeetuna
      auth:
        user: jean-baptiste-emmanuel
        password: Zorg!
```
