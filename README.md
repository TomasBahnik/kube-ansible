# kube-ansible
Manage k8s by Ansible

## Install and test

* install [Miniconda](https://docs.conda.io/en/latest/miniconda.html)

```shell
conda env remove --name kube-ansible
conda create --name kube-ansible -c conda-forge python=3.11
conda activate kube-ansible
pip install ansible
# poetry installed by pip inside the conda env
# pip install poetry
# poetry install
# pytest -svv
```

