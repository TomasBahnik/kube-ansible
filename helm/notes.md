Examples from https://github.com/Masterminds/learning-helm.git and the book

## Drupal

* https://github.com/bitnami/charts/tree/main/bitnami/drupal
  LoadBalancer is used in
  Change `LoadBalancer` to `ClusterIP` for Minikube/microK8s as in Pulumi via `--set service.type=ClusterIP`

```shell
export REGISTRY_NAME=registry-1.docker.io
export REPOSITORY_NAME=bitnamicharts
# helm install my-release   --set service.type=ClusterIP,drupalUsername=admin,drupalPassword=password,mariadb.auth.rootPassword=secretpassword     oci://$REGISTRY_NAME/$REPOSITORY_NAME/drupal
helm install my-drupal  oci://$REGISTRY_NAME/$REPOSITORY_NAME/drupal -f /home/toba/git/github/kube-playground/helm/drupal.values.yaml
```

```text
microk8s kubectl get all
NAME                             READY   STATUS    RESTARTS   AGE
pod/my-drupal-7994fd4b4d-sbxqs   1/1     Running   0          7m26s
pod/my-drupal-mariadb-0          1/1     Running   0          7m26s

NAME                        TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
service/kubernetes          ClusterIP      10.152.183.1     <none>        443/TCP                      2d23h
service/my-drupal           LoadBalancer   10.152.183.22    <pending>     80:31399/TCP,443:32173/TCP   7m26s
service/my-drupal-mariadb   ClusterIP      10.152.183.161   <none>        3306/TCP                     7m26s

NAME                        READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/my-drupal   1/1     1            1           7m26s

NAME                                   DESIRED   CURRENT   READY   AGE
replicaset.apps/my-drupal-7994fd4b4d   1         1         1       7m26s
```

```shell
microk8s kubectl port-forward --namespace default svc/my-drupal 8080:80
```

Works as well 
* `microk8s kubectl port-forward -n default service/my-drupal 8080:80`
* `microk8s kubectl port-forward pod/my-drupal-7994fd4b4d-sbxqs 8080 80` - with errors
 `[unable to create listener: Error listen tcp4 127.0.0.1:80: bind: permission denied unable to create listener: Error listen tcp4 192.168.1.115:80: bind: permission denied unable to create listener: Error listen tcp6 [::1]:80: bind: permission denied]` 

After 
* `microk8s kubectl port-forward --address localhost,192.168.1.115 pod/my-drupal-7994fd4b4d-sbxqs 8080 80`

Clean way is 
```text
microk8s kubectl port-forward --address localhost,192.168.1.115 service/my-drupal 8080:80
Forwarding from 127.0.0.1:8080 -> 8080
Forwarding from 192.168.1.115:8080 -> 8080
Forwarding from [::1]:8080 -> 8080
```

http://192.168.1.115:8080

http://127.0.0.1:8080/ (admin/password)