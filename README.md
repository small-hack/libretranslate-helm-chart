# LibreTranslate Helm Chart
<a href="https://github.com/small-hack/libretranslate-helm-chart/releases"><img src="https://img.shields.io/github/v/release/small-hack/libretranslate-helm-chart?style=plastic&labelColor=blue&color=green&logo=GitHub&logoColor=white"></a>

This Helm chart deploys a LibreTranslate instance on a Kubernetes cluster using the Helm package manager. This is a fork of [libretranslate/helm](https://github.com/libretranslate/helm) with some quality of life updates.

### Prerequisites

- Kubernetes 1.30+
- Helm 3.16+

## Updates from the forked repo include

- using an existing Persistent Volume Claim
  - we now use `persistence.db.existingClaim` and `persistence.models.existingClaim` instead of relying on the ReadWriteMany check
- set a default api key
  - using an existing Kubernetes Secret for a default API key
- add automatic release notes in the GitHub Releases
- use exact `appVersion` for the current version of the LibreTranslate docker image
- renovateBot is used to keep the dependencies of everything in this repo up to date

We will try to submit all of these changes upstream if the repo becomes maintained again.

## Setup helm chart repository

```bash
helm repo add libretranslate https://small-hack.github.io/libretranslate-elm-chart/
helm repo update
helm search repo libretranslate
```

## Installing the Chart

To install the chart with the release name `libretranslate`:

```bash
helm install libretranslate libretranslate/libretranslate --namespace libretranslate --create-namespace
```

This command deploys LibreTranslate on the Kubernetes cluster with the default configuration. The [values.yaml](charts/libretranslate/values.yaml) file lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `libretranslate` deployment:

```bash
helm uninstall libretranslate
kubectl delete namespace libretranslate
```

These commands remove all the Kubernetes components associated with the chart and deletes the release.

## Configuration

See [values.yaml](charts/libretranslate/values.yaml) for the full list of parameters that can be configured. You can specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```bash
helm install libretranslate libretranslate/libretranslate --namespace libretranslate --create-namespace --set service.port=8080
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
helm install libretranslate libretranslate/libretranslate --namespace libretranslate --create-namespace -f values.yaml
```

## Upgrade

Run the following command to upgrade your LibreTranslate installation. This command will use the Helm chart, apply the custom values from values.yaml, and deploy the upgrade to the `libretranslate` namespace:

```bash
helm upgrade --install libretranslate libretranslate/libretranslate --namespace libretranslate -f values.yaml
```

> **Tip**: You can use the default [values.yaml](charts/libretranslate/values.yaml)

# References
- [https://jmrobles.medium.com/libretranslate-your-own-translation-service-on-kubernetes-b46c3e1af630](https://jmrobles.medium.com/libretranslate-your-own-translation-service-on-kubernetes-b46c3e1af630)
- [https://github.com/LibreTranslate/LibreTranslate](https://github.com/LibreTranslate/LibreTranslate)
