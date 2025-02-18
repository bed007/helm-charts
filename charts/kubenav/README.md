# kubenav

A Helm chart for creating the required RBAC for kubenav

## TL;DR;

```console
helm repo add christianknell https://christianknell.github.io/helm-charts
helm repo update
helm install my-release christianknell/kubenav
```

## Introduction

This chart bootstraps RBAC rules for [kubenav](https://github.com/kubenav/kubenav) on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.24+

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm repo add christianknell https://christianknell.github.io/helm-charts
helm repo update
helm install my-release christianknell/kubenav
```

These commands deploy the RBAC settings on the Kubernetes cluster in the default configuration. The [Values](#values) section lists the values that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall the `my-release` deployment:

```console
helm uninstall my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Values

| Key                        | Type   | Default      | Description                                                                                                             |
| -------------------------- | ------ | ------------ | ----------------------------------------------------------------------------------------------------------------------- |
| fullnameOverride           | string | `""`         | String to fully override `"kubenav.fullname"`                                                                           |
| nameOverride               | string | `""`         | Provide a name in place of `kubenav`                                                                                    |
| rbac.customPermissions     | list   | `[]`         | Define the custom permissions to be granted to kubenav                                                                  |
| rbac.mode                  | string | `"readonly"` | Decide which access mode should be granted to kubenav: `readonly`, `cluster-admin` or `custom`.                         |
| rbac.namespaceLimits       | list   | `[]`         | Define a list of namespaces to limit kubenav to only access these namespaces                                            |
| serviceAccount.annotations | object | `{}`         | Annotations to add to the service account                                                                               |
| serviceAccount.create      | bool   | `true`       | Specifies whether a service account should be created                                                                   |
| serviceAccount.name        | string | `""`         | The name of the service account to use. If not set and create is true, a name is generated using the fullname templatev |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```console
helm install my-release -f values.yaml christianknell/kubenav
```
