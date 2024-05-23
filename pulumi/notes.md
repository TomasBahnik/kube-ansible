## Pulumi

* [quickstart](quickstart) is pulumi kube project
* [my_second_app](my_second_app) is pulumi docker project

* https://www.pulumi.com/docs/clouds/kubernetes/get-started/ `curl -fsSL https://get.pulumi.com | sh`
* `~/.pulumi/bin/pulumi`

### Login to Pulumi cloud
`toba65, H...B...!1`

###
New venv installed in `pulumi/quickstart/venv`. There is `pulumi/quickstart/requirements.txt`
Setup project SDK to point
```text
(venv) (base) toba@inspiron-15-7000:~/git/github/kube-playground$ which python
/home/toba/git/github/kube-playground/pulumi/quickstart/venv/bin/python
```

After `pulumi config set isMinikube true` in project dir `Pulumi.playground.yaml` file was created

credentials in `~/.pulumi/credentials`

### Access to nginx
`pulumi up`

```text
microk8s kubectl get all
NAME                                  READY   STATUS    RESTARTS   AGE
pod/nginx-ff93a038-7854ff8877-nhhbs   1/1     Running   0          10m

NAME                     TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)   AGE
service/kubernetes       ClusterIP   10.152.183.1     <none>        443/TCP   3d
service/nginx-f27f4f24   ClusterIP   10.152.183.181   <none>        80/TCP    10m

NAME                             READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/nginx-ff93a038   1/1     1            1           10m

NAME                                        DESIRED   CURRENT   READY   AGE
replicaset.apps/nginx-ff93a038-7854ff8877   1         1         1       10m
```

`microk8s kubectl port-forward --address localhost,192.168.1.115 service/nginx-f27f4f24 8080:80`
http://192.168.1.115:8080/

`pulumi destroy`

## Quickstart
* `cd pulumi/quickstart/`
* `source venv/bin/activate`
* `python = kube-playground/pulumi/quickstart/venv/bin/python`
* change project setting SDK to the above

Install to k8s cluster
```text
pulumi up
Previewing update (playground)


     Type                              Name                   Plan       
 +   pulumi:pulumi:Stack               quickstart-playground  create     
 +   ├─ kubernetes:apps/v1:Deployment  nginx                  create     
 +   └─ kubernetes:core/v1:Service     nginx                  create     

Outputs:
    ip: "10.152.183.0"

Resources:
    + 3 to create

Do you want to perform this update? yes
```