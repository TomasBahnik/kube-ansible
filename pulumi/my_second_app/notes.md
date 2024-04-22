Do not manually delete Pulumi project - use `pulumi destroy` and `pulumi stack rm`

Seems `pulumi new kubernetes-python` creates python 3.11 venv while `pulumi new python -y`,  

as used in tutorial with just docker images/containers (https://www.pulumi.com/learn/pulumi-fundamentals/)
with python 3.10 venv i.e. python venv depends on project 

Deactivate base conda env so only pulumi project `venv` is used
```text
conda deactivate -h

DeactivateHelp: usage: conda deactivate [-h]

Deactivate the current active conda environment.
```

The image `pulumi/tutorial-pulumi-fundamentals-database-local` is arm64. For amd64 use `pulumi/tutorial-pulumi-fundamentals-database:latest`

```text
pulumi/tutorial-pulumi-fundamentals-frontend   latest    13d0640228e3   11 months ago   1.13GB
pulumi/tutorial-pulumi-fundamentals-backend    latest    02cb5c67d7d2   11 months ago   943MB
pulumi/tutorial-pulumi-fundamentals-database   latest    fd14f055f112   11 months ago   644MB
```
