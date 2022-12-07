# Installation


## Pre-requisites



## Install with Docker

1. [Install Docker and Compose](https://docs.docker.com/engine/install/ubuntu/)

2. Copy the Custodian directory
```bat
  git clone https://gitlab.com/data-custodian/custodian.git
```

3. Launch the Swiss Data Custodian

```bat
docker compose -f core/ucm/docker-compose.yml up --build
docker compose -f core/acs/docker-compose.yml up --build
docker compose -f core/epp/docker-compose.yml up --build

```

## Install with Kubernetes

1. Install kubectl

```bat
curl -L https://storage.googleapis.com/kubernetes-release/release/v1.22.1/bin/linux/amd64/kubectl -o /bin/kubectl && chmod +x /bin/kubectl
```

2. Install Kompose

```bat
curl -L https://github.com/kubernetes/kompose/releases/download/v1.24.0/kompose-linux-amd64 -o /bin/kompose
```
