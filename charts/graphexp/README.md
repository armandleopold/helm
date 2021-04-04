# Graphexp

Graphexp is a lightweight web interface to explore and display a graph stored in a Gremlin graph database, via the Gremlin server (version 3.2.x, 3.3.x or 3.4.x).

To get more informations :

* [Github Source Code](https://github.com/armandleopold/graphexp)
* [Dockerhub Docker Image](https://github.com/armandleopold/graphexp)

## Prerequisites

1. Have a running [Kubernetes](https://kubernetes.io/docs/setup/) environment
2. Setup [Helm](https://github.com/kubernetes/helm)

## Installing the Chart

Before you can install the chart you will need to add the `armandleopold` repo to [Helm](https://helm.sh/).

```shell
helm repo add armandleopold https://armandleopold.github.io/helm
helm repo update
```

After you've installed the repo you can install the chart.

```shell
helm upgrade --install --namespace default --values ./my-values.yaml my-release armandleopold/graphexp
```

## Configuration

The following table lists the configurable parameters of the chart and their default values.

`config` :

```yaml
config: |

```

`resources` :

```yaml
resources:
  limits:
    cpu: 100m
    memory: 128Mi
  requests:
    cpu: 100m
    memory: 128Mi
```


| Parameter                        | Description                                      | Default                                                             |
|----------------------------------|--------------------------------------------------|---------------------------------------------------------------------|
| `image.replicaCount`             | Number of replicas to create                     | `1`                                                                 |
| `image.repository`               | Image repository.                                | `ghcr.io/armandleopold/graphexp`                                      |
| `image.tag`                      | Image Tag.                                       | `latest`                                                            |
| `image.pullPolicy`               | Image pull policy.                               | `IfNotPresent`                                                      |
| `image.name`                     | Image name                                       | `graphexp`                                                     |
| `image.deployRegistry`           | If the image is stored in a private registry     | `false`                                                             |
| `image.imagePullSecrets`         | Docker registry credentials Secret name          | `registrysecret`                                                    |
| `image.dataSecret`               | Secret storing docker image registry credentials | `{"auths":{"registry.compagny.com":{"password":"","username":""}}}` |
| `service.type`                   | Service Type                                     | `ClusterIP`                                                         |
| `service.targetPort`             | Service Port                                     | `80`                                                                |
| `service.protocol`               | Service Protocol                                 | `TCP`                                                               |
| `ingress.enabled`                | Expose application with ingress                  | `true`                                                              |
| `ingress.hostnames`              | Urls of exposed application                      | `['graphexp.company.com']`                                     |
| `ingress.tls`                    | Array of TLS Hosts                               | `[]`                                                                |
| `ingress.tls[hosts]`             | Host name                                        | `['graphexp.company.com']`                                     |
| `ingress.tls[hosts[secretName]]` | Secret for the current host name                 | `graphexp`                                                     |
| `resources`                      | Resources requirements & limits                  | `See values.yaml`                                                   |
| `config`                         | Config values for Gitlab Monitor                 | `See values.yaml`                                                   |
