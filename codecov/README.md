# Codecov Self Hosted Helm Chart

This helm chart can be used to deploy the Codecov Self Hosted application to 
a Kubernetes cluster.  It assumes you will provide external dependencies,
including a PostgreSQL and Redis database, and an S3-compatible object store
such as Minio.

## Prerequisites

- A working [kubernetes cluster](https://kubernetes.io/docs/home/)
- [helm](https://helm.sh/docs/) configured to access your cluster

## Required services

- A PostgreSQL v10+ server configured to allow connections from your k8s cluster. 
- A Redis server configured to allow connections from your k8s cluster.
- An S3-compatible object store such as [minio](https://min.io/download).

## Parameters

Additional configuration including the number of web, api, and worker replicas and
their CPU and memory limits can be tuned by overriding `values.yaml`.  See
[codecov/values.yaml](./codecov/values.yaml) for the
available variables.

## Installation

```
helm install codecov --values ./codecov/values.yaml ./codecov
```

## Upgrade

```
helm upgrade codecov ./codecov
```

## Demo
In the demo.yaml file are basic, non production, non secure deployments for the underlying services needed to run Codecov. This is meant for DEMO purposes only (such as a quick POC or to test this chart). If you use the demo for production... you are doing it wrong. We offer no warranty or guarantee of any level of service.
```
# TO use nginx ingress
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.1.2/deploy/static/provider/cloud/deploy.yaml

# TO install Codecov
helm install codecov-demo --values ./codecov/demo.yaml ./codecov
# TO update Codecov
helm upgrade codecov-demo ./codecov/ -f ./codecov/demo.yaml
```