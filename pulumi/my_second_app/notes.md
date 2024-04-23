Do not manually delete Pulumi project - use `pulumi destroy` and `pulumi stack rm`

`pulumi new ...` uses currently active conda env for `python` `python3` 

```text
(venv) toba@inspiron-15-7000:~/git/github/kube-playground/pulumi/quickstart/venv/bin$ ls -la
total 68
drwxrwxr-x 2 toba toba 4096 dub 19 16:53 .
drwxrwxr-x 5 toba toba 4096 dub 19 16:53 ..
-rw-rw-r-- 1 toba toba 1729 dub 19 16:53 activate
-rw-rw-r-- 1 toba toba  953 dub 19 16:53 activate.csh
-rw-rw-r-- 1 toba toba 2233 dub 19 16:53 activate.fish
-rw-rw-r-- 1 toba toba 9033 dub 19 16:53 Activate.ps1
-rwxrwxr-x 1 toba toba 2512 dub 19 16:53 get_gprof
-rwxrwxr-x 1 toba toba 1706 dub 19 16:53 get_objgraph
-rwxrwxr-x 1 toba toba  288 dub 19 16:53 normalizer
-rwxrwxr-x 1 toba toba  277 dub 19 16:53 pip
-rwxrwxr-x 1 toba toba  277 dub 19 16:53 pip3
-rwxrwxr-x 1 toba toba  277 dub 19 16:53 pip3.11
-rwxrwxr-x 1 toba toba  260 dub 19 16:53 pysemver
lrwxrwxrwx 1 toba toba    7 dub 19 16:53 python -> python3
lrwxrwxrwx 1 toba toba   54 dub 19 16:53 python3 -> /home/toba/miniconda3/envs/kube-playground/bin/python3
lrwxrwxrwx 1 toba toba    7 dub 19 16:53 python3.11 -> python3
-rwxrwxr-x 1 toba toba  642 dub 19 16:53 undill
-rwxrwxr-x 1 toba toba  263 dub 19 16:53 wheel
```

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
