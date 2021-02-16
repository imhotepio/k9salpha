---
layout: section
---

<i class="icon fas fa-tachometer-alt fa-7x"></i>

<br/>
<br/>
<br/>

# Benchmarks

<br/>

## <img src="/assets/sections/overview.png" width="auto" height="32"/> Overview

K9s𝞪 integrates [Hey](https://github.com/rakyll/hey) from the brilliant and super talented [Jaana Dogan](https://github.com/rakyll). `Hey` is a CLI tool to benchmark HTTP endpoints similar to AB bench. This feature allows you to benchmark web based containers and services to provide insights on performance objectives and resources settings.

To setup a port-forward, you will need to navigate to the PodView, select a pod and a container that exposes a given port. Using `SHIFT-F` a dialog comes up to allow you to specify a local port to forward to. Once acknowledged, you can navigate to the PortForward view by pressing `f` on the forwarded pod. Selecting a port-forward and using `b` will run a benchmark on that HTTP endpoint. To view your benchmark results, press `<ENTER>` on the port-forward.
To view go all benchmarks enter the command `:bench`. You should now be able to select a benchmark and view the run stats details by pressing `<ENTER>` on your selection.

> NOTE! Port-forwards only last for the duration of the K9s𝞪 session and will be terminated upon exit.

All benchmarks will run with the following defaults:

* Concurrency Level: 1
* Number of Requests: 200
* HTTP Verb: GET
* Path: /

The PortForward view is backed by a K9s𝞪 `benchmarks.yaml` file located relative to your Kubernetes context.
For example `$HOME/.config/k9s-alpha/contexts/contextA/benchmarks.yaml` defines benchmark configurations for contextA.
Each cluster you connect to will have its own benchmark config file. Changes to this file should automatically update the PortForward view to indicate how you want to run your benchmarks.

<br/>
<div class="note">
  <i class="fas fa-skull"></i> Please keep in mind this file will likely change in subsequent releases!
</div>

<br/>

## <img src="/assets/sections/examples.png" width="auto" height="32"/> Example

```yaml
# $HOME/.config/k9s-alpha/contexts/contextA/benchmarks.yaml
benchmarks:
  # Indicates the default concurrency and number of requests setting if a container or service rule does not match.
  defaults:
    # Overrides concurrent connection. Default is 1
    concurrency: 2
    # Overrides the number of requests that will be sent to an endpoint. Default is 200
    requests: 1000
  containers:
    # Containers section allows you to configure your http container's endpoints and benchmarking settings.
    # NOTE: the container ID syntax uses namespace/pod-name:container-name
    default/nginx:nginx:
      # Benchmark a container named nginx by calling the post method on endpoint http://localhost:port/bozo.
      concurrency: 1
      requests: 10000
      http:
        # Specifies the target route. Default is /
        path: /bozo
        # Specifies the http method. Default is GET
        method: POST
        # Sets the request body. Default is empty
        body:
          {"fred":"blee"}
        # Set headers information. Default is empty
        header:
          Accept:
            - text/html
          Content-Type:
            - application/json
  # Similarly you can benchmark an HTTP service exposed either via NodePort or LoadBalancer types.
  services:
    # Service ID is ns/svc-name
    default/nginx:
      # Set the concurrency level
      concurrency: 5
      # Number of requests to be sent
      requests: 500
      http:
        method: GET
        # This setting will depend on whether service is ModePort or LoadBalancer. NodePort may require vendor port tunneling setting.
        # Set this to a node if ModePort or LB if applicable. IP or DNS name.
        host: 1.2.3.4
        path: /bumblebeetuna
      auth:
        user: jean-baptiste-emmanuel
        password: Zorg!
```
