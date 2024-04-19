Apply group modification from https://microk8s.io/docs/getting-started (reboot)

Store kube config from `microk8s config` in `~/.kube/config` : Intellij Kubernetes plugin works

## Sample commands

* `microk8s kubectl get all --all-namespaces` (`microk8s kubectl` == `microk8s.kubectl`)
* `microk8s kubectl create deployment nginx --image=nginx` (and `delete`)
