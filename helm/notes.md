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

```shell
kubectl port-forward --namespace default svc/my-release-drupal 8080:80
```

http://127.0.0.1:8080/ (admin/password)