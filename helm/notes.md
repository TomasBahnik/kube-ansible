Examples from https://github.com/Masterminds/learning-helm.git and the book

LoadBalancer is used in 
```text
drupal/templates/svc.yaml
apiVersion: v1
kind: Service
...
spec:
  type: LoadBalancer
```

Try to change LoadBalancer to ClusterIP for Minikube/microK8s as in Pulumi via `--set service.type=ClusterIP`

```text
helm install mysite bitnami/drupal --set service.type=ClusterIP --version 12.5.13
helm install mysite oci://registry-1.docker.io/bitnamicharts/drupal --set service.type=ClusterIP
```
MariaDB fails to start `find: '/docker-entrypoint-startdb.d/': No such file or directory`. 
There is `drwxr-xr-x   2 root root 4096 Apr  2 18:35 docker-entrypoint-initdb.d`