# Installation


## Pre-requisites



## Installing with docker

1. [Install docker and docker-compose](https://docs.docker.com/engine/install/ubuntu/)

2.  Copy the Custodian Directory
```bat
  git cLone https://gitlab.com/data-custodian/custodian.git
```

3. Install the Swiss Data Custodian

```bat
docker compose -f core/ucm/docker-compose.yml up --build
docker compose -f core/acs/docker-compose.yml up --build
docker compose -f core/epp/docker-compose.yml up --build

```

## Installing with Kubernetes

1. Install Kompose

```bat
curl -L https://storage.googleapis.com/kubernetes-release/release/${CI__KU_VERSION}/bin/linux/amd64/kubectl -o /bin/kubectl && chmod +x /bin/kubectl
```
