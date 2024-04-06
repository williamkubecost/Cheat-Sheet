# Cheat Sheet

More or less, just a few things I tend to use everyday. 

## Tmux

- My defaults are not the same as below, my prefix key for example is `C-f`, split panes is `prefix + |`, and vertical panes is `prefix + -` 
- `C-b`: CTRL + b, press these two at the same time and then release. This is done before attempting other bindings!
- `C-b <release> %`: Splits the panes left & right
- `C-b <release> "`: Splits the panes top & bottom
- `C-b <release> <arrow-key>`: Navigate back and forth
- `C-b <release> D`: Close a pane
- `C-b <release> c`: Create a second virtual window
- `C-b <release> p`: Go back to the previous window; `n`: Go to the next window
- `tmux ls`: List sessions
- `tmux attach -t 0`: Connects you to a session
- `tmux source-file ~/.tmux.conf` this seems to work 
- [Dracula Theme](https://dev.to/andrenbrandao/terminal-setup-with-zsh-tmux-dracula-theme-48lm)
- More Tmux preffered settings -> [link](https://hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)

## Linux

#### Process Management

- `pgrep`
- `pkill`
- `ps aux`

#### Network

- `openssl x509 -in <cert-path> -noout -text` inspect certificate
- `curl http://<IP>:<PORT>`
- `dig` dns query tool
- `ping`, `traceroute`, `nc -vz host port`, at a minimum everyone should know these
- Nice guide from Cloudflare, troubleshooting [ERR_TOO_MANY_REDIRECTS](https://developers.cloudflare.com/ssl/troubleshooting/too-many-redirects/)

#### Git

- `git checkout -b <branch-name>` creates a new branch
- `git push --set-upstream origin <branch-name>` push to specific branch
- `git log` check logs for branch/repo

## Kubernetes

#### Kubectl

- `kubectl get pods` basic
- `kubectl get svc` basic
- `kubectl get nodes`basic
- `kubectl get svc` basic
- `kubectl get ep` basic
- `kubectl describe <resources>` basic
- `-o wide` basic
- `-o yaml` basic
- `kubectl port-forward deployment/name port` Port forward to specific app/service
- `kubectx` easy way to change context, needs to be [installed](https://github.com/ahmetb/kubectx)
- `kubens` easy way to change ns, needs to be [installed](https://github.com/ahmetb/kubectx/blob/master/kubens)
- `kubectl rollout restart deploy <deploy-name> -n <ns>`
- `kind create cluster --image "kindest/node:v1.20.15"`

#### Helm

- `helm package .` --> packages helm chart locally
- `helm package CHART_PATH` --> packages chart in specific path
- `helm push CHART_PACKAGE oci://REPO_URL/REPO`
- `helm install RELEASE_NAME /path/to/local/chart.tgz`
- `helm template <release-name> --values <values-file> > rendered-values.yaml` generates YAML manifests, good for testing helm chart changes are templating correctly
- This was a cool trick to pull a local helm repo: https://github.com/rancher/rancher/issues/43092#issuecomment-1845065503

#### Istio

- `istioctl analyze -n <namespace>`
- `kubectl logs <istio-proxy-pod> -c istio-proxy -n <namespace>`
- `istioctl x describe pod <pod-name>` you need to change NS context
- Just a general reminder to check istio [permissive](https://istio.io/latest/docs/concepts/security/#permissive-mtls) and [not permissive](https://istio.io/latest/docs/concepts/security/#strict-mtls).
- `traffic.sidecar.istio.io/excludeInboundPorts` exclude from Envoy

#### Rancher

- Reset admin pw `kubectl -n cattle-system exec $(kubectl -n cattle-system get pods -l app=rancher --no-headers | head -1 | awk '{ print $1 }') -c rancher -- reset-password`

#### Docker
- `docker images`
- `docker ps` --> show running containers
- `docker inspect <image-id>`
- `docker login`
- `docker exec -ti <container-id> bash` --> open a shell on a container
- `docker tag SOURCE_IMAGE[:TAG] REPO_URL/REPO_NAME/REPOSITORY[:TAG]`
- `docker push REPO_URL/REPO_NAME/REPOSITORY[:TAG]`

#### ssh 

- `ssh-copy-id <un>@<ip>`
