# K9s𝞪 Community Plugins

K9s𝞪 plugins extend the tool to provide additional functionality via actions to further help you observe or administer your Kubernetes clusters.

| Plugin-Name     | Description                      | Available on Views | Shortcut | Kubectl plugin, external dependencies                                                 |
|-----------------|----------------------------------|--------------------|----------|---------------------------------------------------------------------------------------|
| log_stern.yml   | View resource logs using stern   | pods               | Ctrl-l   |                                                                                       |
| log_jq.yml      | View resource logs using jq      | pods               | Ctrl-j   | kubetcl-plugins/kubectl-jq                                                            |
| job_suspend.yml | Suspends a running cronjob       | cronjobs           | Ctrl-s   |                                                                                       |
| dive.yml        | Dive image layers                | containers         | d        | [Dive](https://github.com/wagoodman/dive)                                             |
| get-all.yml     | get all resources in a namespace | all                | g        | [Krew](https://krew.sigs.k8s.io/), [ketall](https://github.com/corneliusweig/ketall/) |

<hr/>

<img src="assets/imhotep_logo.png" width="32" height="auto" alt="Imhotep"/> &nbsp;© 2021 Imhotep Software LLC. All materials licensed under [Apache v2.0](http://www.apache.org/licenses/LICENSE-2.0)
