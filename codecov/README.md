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
[codecov/values.yaml](/codecov/values.yaml) for the
available variables.

## Installation

```
helm install codecov --values ./codecov/values.yaml ./codecov
```

## Upgrade

```
helm upgrade codecov .
```