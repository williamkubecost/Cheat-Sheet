# Cheatsheet


### Tmux

- `C-b`: CTRL + b, press these two at the same time and then release. This is done before attempting other bindings!
- `C-b <release> %`: Splits the panes left & right
- `C-b <release> "`: Splits the panes top & bottom
- `C-b <release> <arrow-key>`: Navigate back and forth
- `C-b <release> D`: Close a pane
- `C-b <release> c`: Create a second virtual window
- `C-b <release> p`: Go back to the previous window; `n`: Go to the next window
- `tmux ls`: List sessions
- `tmux attach -t 0`: Connects you to a session

### Kubernetes

#### kubectl
- `kubectl port-forward deployment/name port` Port forward to specific app/service
- `kubectx` easy way to change context, needs to be installed
- `kubens` easy way to change ns, needs to be installed
- `kubectl rollout restart deploy <deploy-name> -n <ns>`

#### helm
- `helm package .` packages helm chart locally
- `helm template <release-name> --values <values-file> > rendered-values.yaml` generates YAML manifests, good for testing helm chart changes are templating correctly

#### istio
- `istioctl analyze -n <namespace>`
- `kubectl logs <istio-proxy-pod> -c istio-proxy -n <namespace>`
- `istioctl x describe pod <pod-name>` you need to change NS context
- Just a general reminder to check istio [permissive](https://istio.io/latest/docs/concepts/security/#permissive-mtls) and [not permissive](https://istio.io/latest/docs/concepts/security/#strict-mtls).

