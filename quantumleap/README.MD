# CrateDB Helm Chart

This directory contains a Kubernetes chart to deploy a [Quantum Leap](https://github.com/smartsdk/ngsi-timeseries-api) cluster using Deployment.

## Prerequisites Details
* Kubernetes 1.5+
* PV support on the underlying infrastructure

## Todo
* 

## Chart Details
This chart will do the following:

* Implement a HA scalable Quantum Leap cluster using a Kubernetes Deployment.

## Installing the Chart

To install the chart with the release name `my-release`:

```console
$ helm repo add oc https://orchestracities.github.io/charts/
$ helm dependency update
$ helm install --name my-release oc/quantumleap
```

## Connecting to QuantumLeap


## Configuration

The following table lists the configurable parameters of the patroni chart and their default values.

|       Parameter                   |           Description                       |                         Default                     |
|-----------------------------------|---------------------------------------------|-----------------------------------------------------|
| `replicaCount`                    | Amount of pods to spawn                     | `3`                                                 |
| `image.repository`                | The image to pull                           | `smartsdk/quantumleap`                              |
| `image.tag`                       | The version of the image to pull            | `0.4.1`                                             |
| `image.pullPolicy`                | The pull policy                             | `IfNotPresent`                                      |
| `resources`                       | Any resources you wish to assign to the pod | `{}`                                                |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```console
$ helm install --name my-release -f values.yaml oc/quantumleap
```

> **Tip**: You can use the default [values.yaml](values.yaml)

## Cleanup

To remove the spawned pods you can run a simple `helm delete <release-name>`.

Helm will however preserve created persistent volume claims,
to also remove them execute the commands below.

```console
$ release=<release-name>
$ helm delete $release
$ kubectl delete pvc -l release=$release
```
